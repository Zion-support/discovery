# 📨 Discovery Results — Instant Dual Email Delivery

**Rule:** the moment a visitor submits the free AI Discovery questionnaire (https://ziontechgroup.com/discovery/), the personalized results are emailed to **both**:

1. **The client** — at the email they entered in the questionnaire
2. **Zion commercial team** — `commercial@ziontechgroup.com`

No delay, no batching. Discovery is always online and always free.

## How it works

1. Questionnaire front-end (`/discovery/`) collects answers + email and POSTs the payload to the discovery intake endpoint.
2. The intake validates and scores the answers, builds the personalized report (app shortlist + ROI snapshot + pilot roadmap mapped to the Zion AI App Network).
3. The report is rendered to HTML email and sent simultaneously to client + `commercial@ziontechgroup.com` via the mail provider (SMTP secrets below).
4. A fallback path fires `repository_dispatch` → `.github/workflows/discovery-results-email.yml` which re-sends the report if the primary sender fails (guaranteed delivery).
5. Every submission is appended to `leads/` (deduplicated — see `append_leads.py`) so commercial has a durable CRM trail.

## Secrets required (repo Settings → Secrets)
- `SMTP_SERVER`, `SMTP_PORT`, `SMTP_USERNAME`, `SMTP_PASSWORD`
- `DISCOVERY_FROM_EMAIL` (e.g. discovery@ziontechgroup.com)
- `COMMERCIAL_EMAIL` = commercial@ziontechgroup.com

## SLA
- Delivery target: < 60 seconds from submit.
- If either recipient fails, the workflow retries 3× and opens an issue in this repo tagged `discovery-delivery`.

## Links
- Questionnaire: https://ziontechgroup.com/discovery/
- Benefits: https://ziontechgroup.com/app-network-discovery-benefits.html
- Network hub: https://github.com/Zion-support/zion-network
