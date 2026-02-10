# Publish QSA Landing to qsa.quankey.xyz

**Goal:** Make the QSA landing page accessible at `https://qsa.quankey.xyz` with a valid TLS certificate.

**Current state (2026-02-10):**
- GitHub Pages: ENABLED, source `main /`, status BUILT
- Custom domain `qsa.quankey.xyz`: CONFIGURED in repo settings
- DNS CNAME: CORRECT (`qsa.quankey.xyz` -> `jcquankey.github.io`)
- HTTP: WORKS (200 OK, correct content)
- HTTPS: BROKEN (GitHub serving `*.github.io` cert, not a custom domain cert)
- `https_enforced`: false

---

## What needs to happen

GitHub must provision a Let's Encrypt certificate for `qsa.quankey.xyz`. This is normally automatic but may need a manual trigger.

**Sequence:** DNS is already done. Only GitHub Pages settings need attention.

---

## JC Steps (GitHub UI)

### Step 1: Force cert re-provisioning

1. Open: https://github.com/JCQuankey/quankey-qsa-landing/settings/pages
2. Under **Custom domain**, you should see `qsa.quankey.xyz`
3. Look for a status message. Possible states:
   - "DNS check successful" + "Enforce HTTPS" checkbox available -> Go to Step 2
   - "DNS check in progress" -> Wait 15 minutes, refresh
   - "DNS check failed" or no cert status -> Do Step 1a below

#### Step 1a: Toggle custom domain (only if cert is stuck)

1. Clear the **Custom domain** field and click **Save**
2. Wait 10 seconds
3. Re-enter `qsa.quankey.xyz` in the **Custom domain** field and click **Save**
4. Wait for the DNS check to complete (green checkmark)
5. GitHub will begin provisioning a Let's Encrypt cert (can take 5-30 minutes)

### Step 2: Enable Enforce HTTPS

1. Once the cert is provisioned, the **Enforce HTTPS** checkbox becomes available
2. Check the **Enforce HTTPS** box
3. Click **Save** (if needed)

### Step 3: Verify other settings are correct

- **Source:** Deploy from a branch
- **Branch:** `main` / `/ (root)`
- **Custom domain:** `qsa.quankey.xyz`
- **Enforce HTTPS:** checked

---

## DNS (Hostinger) -- ALREADY DONE

The CNAME record is already configured correctly. **Do NOT change DNS.**

For reference, the record is:

| Type | Host/Name | Target | TTL |
|------|-----------|--------|-----|
| CNAME | qsa | jcquankey.github.io | default |

**Warning:** Do NOT add a wildcard record (`*.quankey.xyz`) -- this creates subdomain takeover risk.

---

## Verification Commands

Run these after completing the GitHub UI steps. Wait at least 15 minutes after Step 1a (if needed).

```bash
# 1. Confirm DNS still resolves
dig qsa.quankey.xyz CNAME +short
# Expected: jcquankey.github.io.

# 2. Check HTTPS works with valid cert
curl -sI https://qsa.quankey.xyz/ | head -5
# Expected: HTTP/2 200

# 3. Confirm correct content is served
curl -s https://qsa.quankey.xyz/ | grep -i "Quankey QSA"
# Expected: line(s) containing "Quankey QSA"

# 4. Check cert subject (should NOT be *.github.io)
curl -svI https://qsa.quankey.xyz/ 2>&1 | grep "subject:"
# Expected: subject: CN=qsa.quankey.xyz  (or a SAN including it)
# Bad:      subject: CN=*.github.io      (cert not provisioned yet)

# 5. Confirm HTTP redirects to HTTPS (after Enforce HTTPS is on)
curl -sI http://qsa.quankey.xyz/ | head -3
# Expected: HTTP/1.1 301 ... Location: https://qsa.quankey.xyz/
```

---

## What "good" looks like

| Check | Expected |
|-------|----------|
| `https://qsa.quankey.xyz/` in browser | Page loads with padlock, Quankey QSA content visible |
| `http://qsa.quankey.xyz/` in browser | Redirects to HTTPS automatically |
| Contact link | Clicking "Request a pilot" opens email to jcano@cainmani.com |
| Certificate | Valid Let's Encrypt cert for qsa.quankey.xyz (not *.github.io) |

---

## Troubleshooting

| Symptom | Cause | Fix |
|---------|-------|-----|
| "Enforce HTTPS" grayed out | Cert still provisioning | Wait 30 min, then try Step 1a |
| DNS check fails in GitHub UI | Stale cache | Wait 10 min, refresh page |
| HTTPS works but shows wrong content | Branch misconfigured | Verify source is `main` / `/ (root)` |
| Browser shows cert warning | Cert covers *.github.io not custom domain | Do Step 1a to force re-provision |
| "404 There isn't a GitHub Pages site here" | Pages not enabled | Re-enable: source `main` / `/ (root)` |

---

*Last updated: 2026-02-10*
