# Persistent Petitioner Helm chart

Deploy petition automation with IMAP email and optional Playwright signing.

## Secrets

Create a Secret (or use External Secrets / 1Password) with:

- `EMAIL_IMAP_HOST`, `EMAIL_USER`, `EMAIL_PASSWORD` — IMAP credentials
- `USER_FIRST_NAME`, `USER_LAST_NAME`, `USER_EMAIL`, `USER_ZIP_CODE` — form fill data
- `USER_PHONE` (optional)
- `DATABASE_URL` (optional; defaults to SQLite in `/app/data`)
- `AUTOMATION_ENABLED` (optional; set to `true` to enable Playwright signing)

## Setup requirements

- **Credentials:** 1Password item or ExternalSecret with IMAP and form-fill fields.
- **Email forwarding:** Forward petition emails to a dedicated inbox (e.g. Gmail) and use App Password for IMAP.

## Install

```bash
helm install persistent-petitioner . -n persistent-petitioner --create-namespace -f my-values.yaml
```
