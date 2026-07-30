# Persistent Petitioner Helm chart

Deploy petition automation with IMAP email and optional Playwright signing. Designed for PostgreSQL; no persistent storage required.

## 🗺️ Topology

![persistent-petitioner topology](docs/img/topology.svg)

<sub>Generated from this repo’s `values.yaml`, `Chart.yaml` and `argocd/` manifests. Source: [`docs/img/topology.mmd`](docs/img/topology.mmd).</sub>

## Secrets

Create a Secret (or use External Secrets / 1Password) with:

- `DATABASE_URL` — **required**. PostgreSQL connection string, e.g. `postgresql://user:pass@postgres-host:5432/petitions`. Database name should be `petitions`.
- `EMAIL_IMAP_HOST`, `EMAIL_USER`, `EMAIL_PASSWORD` — IMAP credentials
- `USER_FIRST_NAME`, `USER_LAST_NAME`, `USER_EMAIL`, `USER_ZIP_CODE` — form fill data
- `USER_PHONE` (optional)
- `AUTOMATION_ENABLED` (optional; set to `true` to enable Playwright signing)

## Setup requirements

- **PostgreSQL:** Create database `petitions` and add `DATABASE_URL` to the secret.
- **Credentials:** 1Password item or ExternalSecret with IMAP, form-fill, and DATABASE_URL.
- **Email forwarding:** Forward petition emails to a dedicated inbox (e.g. Gmail) and use App Password for IMAP.

## Install

```bash
helm install persistent-petitioner deploy/helm -n persistent-petitioner --create-namespace -f my-values.yaml
```

Argo CD path: `deploy/helm`
