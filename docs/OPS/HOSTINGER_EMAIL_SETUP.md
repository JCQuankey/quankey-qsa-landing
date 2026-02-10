# Hostinger Email Setup: dev@quankey.xyz

**For:** JC (manual steps in Hostinger hPanel)
**Goal:** Set up dev@quankey.xyz and optionally forward to a personal inbox
**Status:** Documentation only -- no infra changes made

---

## Step 0: Determine Your Email Service

Log in to [hPanel](https://hpanel.hostinger.com) and check which email service is active for `quankey.xyz`:

| What you see in hPanel | Your path |
|------------------------|-----------|
| **Emails** section shows "Hostinger Email" | **Path A** (Hostinger native) |
| **Emails** section shows "Titan Email" | **Path B** (Titan / Hostinger Business Email) |
| No email service active | Purchase Hostinger Email or Titan, then follow the relevant path |

---

## Path A: Hostinger Email (MX: mx1/mx2.hostinger.com)

### A1. Create the mailbox
1. hPanel > **Emails** > **Manage** for `quankey.xyz`
2. Click **Create email account**
3. Enter `dev` as the prefix, set a strong password
4. Click **Create**

### A2. Set MX records (if not already set)
1. hPanel > **Domains** > **DNS Zone** for `quankey.xyz`
2. Ensure these MX records exist (and remove any others):

| Type | Name | Priority | Value |
|------|------|----------|-------|
| MX | @ | 5 | mx1.hostinger.com |
| MX | @ | 10 | mx2.hostinger.com |

Source: [Hostinger MX Records Guide](https://support.hostinger.com/en/articles/1583625-how-to-set-up-mx-records-at-hostinger)

### A3. Set SPF record
Add a TXT record (or edit existing):

| Type | Name | Value |
|------|------|-------|
| TXT | @ | `v=spf1 include:_spf.hostinger.com ~all` |

**Important:** Only ONE SPF record per domain. If you already have an SPF record for another service, combine them:
```
v=spf1 include:_spf.hostinger.com include:_other_service.com ~all
```

Source: [Hostinger SPF Setup](https://support.hostinger.com/en/articles/4592632-how-to-add-a-spf-record)

### A4. Enable DKIM
1. hPanel > **Emails** > **Email configuration** for `quankey.xyz`
2. DKIM should auto-generate. Copy the DKIM TXT record and add it to DNS if prompted.

Source: [Hostinger DKIM Guide](https://support.hostinger.com/en/articles/6397806-how-to-set-up-dkim-at-hostinger)

### A5. Set DMARC record (recommended)

| Type | Name | Value |
|------|------|-------|
| TXT | _dmarc | `v=DMARC1; p=quarantine; rua=mailto:dev@quankey.xyz` |

### A6. Set up forwarding (optional)
1. hPanel > **Emails** > **Manage** > select `dev@quankey.xyz`
2. Go to **Email forwarding**
3. Add forwarding address (your personal inbox)
4. Keep a copy in the Hostinger mailbox (recommended for audit trail)

---

## Path B: Titan Email (MX: mx1/mx2.titan.email)

### B1. Create the mailbox
1. hPanel > **Emails** > **Manage** for `quankey.xyz` (opens Titan admin)
2. Click **Add user** or **Create account**
3. Enter `dev` as the prefix, set password

### B2. Set MX records

| Type | Name | Priority | Value |
|------|------|----------|-------|
| MX | @ | 10 | mx1.titan.email |
| MX | @ | 20 | mx2.titan.email |

Source: [Titan MX Records](https://support.titan.email/hc/en-us/articles/360038024254-Setting-up-MX-records-for-Titan)

### B3. Set SPF record

| Type | Name | Value |
|------|------|-------|
| TXT | @ | `v=spf1 include:spf.titan.email ~all` |

### B4. DKIM / DMARC
- Titan provides DKIM setup in the admin panel. Follow the prompts.
- DMARC: same as Path A step A5, but with Titan's guidance for the `rua` address.

Source: [Titan DKIM/DMARC Guide](https://support.titan.email/hc/en-us/articles/900005765843-Email-Authentication-DKIM-DMARC)

### B5. Set up forwarding
1. Titan admin > **Settings** for `dev@quankey.xyz`
2. **Auto-forward** to your personal inbox

---

## Do / Don't

| Do | Don't |
|----|-------|
| Keep only ONE SPF record per domain | Don't add multiple SPF TXT records (causes failures) |
| Remove old MX records from other providers | Don't leave competing MX records (mail loss risk) |
| Test by sending from an external address | Don't assume it works without testing |
| Wait up to 24h for DNS propagation | Don't panic if it doesn't work in 5 minutes |
| Set DKIM before going live | Don't skip DKIM (email will land in spam) |

---

## Verification

After setup, test:
```bash
# Check MX records
dig quankey.xyz MX +short

# Check SPF
dig quankey.xyz TXT +short

# Check DMARC
dig _dmarc.quankey.xyz TXT +short

# Send a test email
echo "Test" | mail -s "QSA test" dev@quankey.xyz
```

Or use: [MXToolbox](https://mxtoolbox.com/SuperTool.aspx?action=mx%3aquankey.xyz) to verify all records.

---

*Documentation only. No DNS or email changes were executed.*
