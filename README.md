Institution Connectivity Health — Live Lookup & Benchmark

A real-time tool to monitor and benchmark bank-connection health across financial institutions — connection type (OAuth vs credential), product coverage, live status, and Transaction Success Rate (TSR) — with a side-by-side comparison view.

The problem

Bank-connection reliability varies widely by institution and by product, but that health signal is scattered and hard to act on. Teams end up reacting to breakages instead of seeing them coming, and comparing providers is guesswork.

What it does
Live search across institutions (type-ahead).
Per-product health — Auth, Balance, Identity, Transactions — as ACTIVE / DEGRADED / DOWN, with Transaction Success Rate (TSR).
Connection type — OAuth (bank-hosted) vs credential-based.
Side-by-side comparison for apples-to-apples benchmarking.
Data fetched live on each lookup — a continuous view, not a snapshot.
How it works
Lightweight Python HTTP server (standard library — no framework).
All provider API calls happen server-side; credentials live in environment variables, never in the codebase.
Access is gated by HTTP Basic Auth so a hosted URL can be shared safely.
Run locally
pip install -r requirements.txt
set PLAID_ENV=production
set PLAID_CLIENT_ID=...        # your production client_id
set PLAID_SECRET=...           # your production secret
set APP_USER=team
set APP_PASSWORD=...           # a strong password you choose
python plaid_server.py
# open http://localhost:8000
Deploy (permanent URL, e.g. Render)
This repo includes render.yaml — Render auto-detects it.
New Web Service → connect this repo.
Set the three secret env vars in the dashboard: PLAID_CLIENT_ID, PLAID_SECRET, APP_PASSWORD.
Deploy → share the resulting https://… URL plus the login.
Tech

Python 3 · standard-library HTTP server · environment-based secrets · Basic-Auth · deployable to any container/PaaS host.
