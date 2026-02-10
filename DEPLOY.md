# Deploy: Quankey QSA Landing Page

This document covers how to publish this landing page to GitHub Pages with a custom domain.

---

## Prerequisites

- GitHub account with access to `JCQuankey` organization/user
- `git` and `gh` CLI installed (or use GitHub web UI)
- Hostinger account for DNS management of `quankey.xyz`

---

## Step 1: Create Public Repository on GitHub

**Option A: Using `gh` CLI**

```bash
cd quankey-qsa-landing
gh repo create JCQuankey/quankey-qsa-landing --public \
  --description "Quankey QSA - Quantum-Safe Assurance Landing Page" \
  --source . --push
```

**Option B: Using GitHub Web UI**

1. Go to https://github.com/new
2. Repository name: `quankey-qsa-landing`
3. Description: `Quankey QSA - Quantum-Safe Assurance Landing Page`
4. Visibility: **Public**
5. Do NOT initialize with README (we already have one)
6. Click **Create repository**
7. Then push from local:

```bash
cd quankey-qsa-landing
git remote add origin https://github.com/JCQuankey/quankey-qsa-landing.git
git push -u origin main
```

---

## Step 2: Enable GitHub Pages

1. Go to https://github.com/JCQuankey/quankey-qsa-landing/settings/pages
2. **Source:** Deploy from a branch
3. **Branch:** `main`
4. **Folder:** `/ (root)`
5. Click **Save**

The default URL will be: `https://jcquankey.github.io/quankey-qsa-landing/`

Wait 1-2 minutes for the first deployment to complete.

---

## Step 3: Set Custom Domain

1. On the same GitHub Pages settings page
2. **Custom domain:** `qsa.quankey.xyz`
3. Click **Save**
4. Check **Enforce HTTPS** (may take a few minutes to become available)

GitHub will verify the CNAME file in the repo matches. The `CNAME` file already contains `qsa.quankey.xyz`.

---

## Step 4: Configure DNS at Hostinger

1. Log in to https://www.hostinger.com (or hpanel.hostinger.com)
2. Go to **Domains** -> `quankey.xyz` -> **DNS / Nameservers** -> **DNS Records**
3. Add a new record:

```
Type:   CNAME
Name:   qsa
Target: jcquankey.github.io
TTL:    3600
```

4. Save the record
5. Wait for DNS propagation (typically under 1 hour)

**Important:** Do NOT modify the existing A record for `quankey.xyz` or any other subdomains. Only add the new `qsa` CNAME.

---

## Step 5: Verify

```bash
# Check DNS propagation
dig qsa.quankey.xyz CNAME +short
# Expected: jcquankey.github.io.

# Check HTTPS
curl -sI https://qsa.quankey.xyz/ | head -5
# Expected: HTTP/2 200

# Verify content
curl -s https://qsa.quankey.xyz/ | grep "Quankey QSA"
# Expected: match

# Verify HTTPS redirect
curl -sI http://qsa.quankey.xyz/ | grep -i location
# Expected: Location: https://qsa.quankey.xyz/
```

---

## Rollback

To take the site down:

1. **Disable GitHub Pages:** Settings -> Pages -> Source: None
2. **Or delete the CNAME record** at Hostinger

To remove the custom domain but keep the site on GitHub Pages:
1. Delete the `CNAME` file from the repo
2. Remove the custom domain setting in GitHub Pages
3. Site remains available at `https://jcquankey.github.io/quankey-qsa-landing/`

---

## Updating the Landing Page

```bash
# Edit index.html locally
# Then commit and push
cd quankey-qsa-landing
git add index.html
git commit -m "Update landing page"
git push
# GitHub Pages auto-deploys within ~60 seconds
```

---

## Security Headers

GitHub Pages provides the following headers by default:
- HTTPS enforcement (after enabling "Enforce HTTPS")
- Standard caching headers

For additional headers (CSP, X-Frame-Options, etc.), consider adding a `_headers` file if migrating to Netlify/Cloudflare Pages in the future. GitHub Pages does not support custom response headers.

---

*Last updated: 2026-02-10*
