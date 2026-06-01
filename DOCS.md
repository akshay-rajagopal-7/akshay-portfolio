# Akshay Rajagopal — Portfolio Project Reference

_Last updated: 1 June 2026_

A single reference for the personal portfolio site, its hosting, the Railway app behind it, and how to maintain everything. Read top to bottom once; after that just jump to the section you need.

---

## 1. What this is

A personal portfolio website for Akshay Rajagopal (Finance · Accounts · Compliance, Dubai UAE). Dark "forensic brutalism" design with an animated, cursor-interactive constellation across the whole hero. It showcases four works and links out to LinkedIn + email.

**Live site:** https://akshay-rajagopal-7.github.io/akshay-portfolio/

The four works featured:
1. **AureviaForge Engine** (Live) — forensic audit analytics platform. Links to the Railway-hosted live app.
2. **Darvin & the Pulse** (Beta) — 3-agent AI review tribunal (Darvin / Ward / Athena), each with a hand-drawn SVG face glyph. Demo "coming soon".
3. **Petty Cash Workbook** — downloadable Excel control model (.xlsx).
4. **Business Process Workflow** — downloadable 17-slide deck (.pptx).

---

## 2. Where everything lives

| Thing | Location |
|---|---|
| Portfolio site (live) | https://akshay-rajagopal-7.github.io/akshay-portfolio/ |
| Portfolio code (GitHub) | https://github.com/akshay-rajagopal-7/akshay-portfolio |
| Portfolio code (Mac) | `~/Documents/akshay-portfolio/` |
| AureviaForge live app | https://aureviaforge-engine-production.up.railway.app |
| AureviaForge code (GitHub) | https://github.com/akshay-rajagopal-7/aureviaforge-engine |
| Darvin tribunal code (GitHub) | https://github.com/akshay-rajagopal-7/aurevia-tribunal |
| Hosting (portfolio) | GitHub Pages — free, no expiry |
| Hosting (AureviaForge) | Railway — Hobby plan, $5/mo |
| Contact email | mr.akshay@aol.com |
| LinkedIn | https://www.linkedin.com/in/a-rajagopal/ |

The portfolio repo contains:
```
akshay-portfolio/
  index.html        (the entire site — one file)
  assets/
    Petty_Cash_Workbook.xlsx
    Business_Process_Workflow.pptx
  DOCS.md           (this file)
```

**The site is always served from `index.html`.** GitHub Pages only serves a file named exactly `index.html`. If you download an updated copy that's named anything else (e.g. `index1.html`, `index (3).html`), you must copy it onto `index.html` in the repo before pushing — never rename the repo file itself.

---

## 3. Current design / layout (so you know what's there)

- **Hero:** huge "AKSHAY" (solid) over "RAJAGOPAL" (green outline). Behind everything, a full-width animated **constellation** — drifting dots + connecting lines, occasional gold "anomaly" clusters, and it reacts to the cursor (nodes pull in + links brighten near the mouse). Below the name: a short bio, "Based in Dubai, UAE", and a "Connect on LinkedIn" button.
- **Platforms section:** two cards — AureviaForge Engine (with a 10-row numbered test ledger) and Darvin & the Pulse (with three agent face glyphs).
- **Documents section:** two cards — Petty Cash Workbook (.xlsx download) and Business Process Workflow (.pptx download).
- **Footer:** big "Let's talk controls." (masks up on scroll), the line "Open to forensic finance, accounting, audit & compliance work", a LinkedIn button, and an email icon (mailto). Copyright row reads "© 2026 Akshay Rajagopal · Built & designed solo, using AI".
- Type: Archivo (display), JetBrains Mono (labels), Fraunces (card titles). Colours: green `#10b981`, gold `#f59e0b`, near-black background.

---

## 4. How to update the portfolio site

The whole site is one file: `index.html`. To change anything (text, design, links):

1. Get the new HTML file (download it — it may arrive named `index.html`, `index1.html`, etc.).
2. In Terminal:
   ```bash
   cd ~/Documents/akshay-portfolio
   cp "$(ls -t ~/Downloads/*.html | head -1)" index.html   # copies the NEWEST .html from Downloads onto index.html
   git add index.html
   git commit -m "describe the change"
   git push
   ```
3. Wait ~90 seconds for GitHub Pages to rebuild.
4. View in a **Safari Private Window** (Cmd+Shift+N) to bypass cache:
   `https://akshay-rajagopal-7.github.io/akshay-portfolio/`

### If the site "looks old" after pushing
It's almost always **browser cache**, not the site. Fixes in order:
1. Add a cache-buster to the URL: `...akshay-portfolio/?v=now`
2. Safari → Develop → Empty Caches (Cmd+Option+E), then Cmd+R
3. Open a Private Window (Cmd+Shift+N) — zero cache, shows the true live version

### Golden rules (learned the hard way)
- The repo file must be named **`index.html`** — that's all GitHub Pages serves. Downloads named otherwise get copied onto `index.html` (the `cp` line above does this).
- A **new repo** must be created in the browser (github.com/new) **before** the first `git push`. "Repository not found" = repo doesn't exist yet.
- Paste web URLs into **Safari**, never the Terminal.
- Before committing, verify you copied the **newest** file: `ls -t ~/Downloads/*.html | head -1`
- The repo must stay **public** or free GitHub Pages stops serving it. **Never delete the repo** — the link dies with it.

---

## 5. Railway — the AureviaForge live app

### Plan & billing
- **Plan:** Hobby — **$5/month flat** (charged regardless of usage).
- **Included usage:** $5/month of compute credit comes _with_ the subscription.
- **Real-world cost:** the app uses ~$1/month of compute, inside the free $5 credit. Expected bill ≈ the **$5 base**, ~$60/year.
- Overage only happens if monthly usage exceeds $5; then you pay the difference.

### Spending caps (already set — these protect you)
Set under **Usage → Set limits / Update limits**:
- **Compute hard limit: $10** — when compute spend hits $10 in a billing cycle, **all resources stop** (app offline until next cycle or you raise it). $10 is the lowest Railway allows.
- **Agent hard limit: $5** — caps Railway's AI-agent feature (unrelated to the app).
- Email alerts notify before a cap is hit.

These caps protect your wallet — worst case the app just switches off, no runaway bill.

### Railway project name
Railway auto-named the project **`aware-wisdom`** (random). That's the project that holds AureviaForge.

### Bring the app back online (after sleep / cap shutoff / trial expiry)
1. railway.com → log in.
2. Left sidebar → **Projects** → open **aware-wisdom**.
3. Click the service tile. If stopped/crashed/sleeping → **Deploy** (or ⋯ → Redeploy / Restart).
4. Wait for **Active** (green).
5. Test: open `https://aureviaforge-engine-production.up.railway.app`
6. If the public URL ever changes after a redeploy, update the "Open live app" link in `index.html` (search for `aureviaforge-engine-production`).

### To stop paying / cancel Railway
Settings → Billing → cancel/downgrade. Then either change the portfolio's "Open live app" button to "demo on request", or move the app to a free host (Render free tier).

---

## 6. IMPORTANT — public upload risk (UNRESOLVED)

**The problem:** AureviaForge currently lets any visitor upload data. Processing large files (e.g. 50 million rows) spikes server CPU/RAM, which:
- costs Railway compute money — heavy use could exceed the $5 credit and hit the $10 cap (app shuts off), and
- lets strangers/bots run expensive jobs on your paid server.

The $10 hard cap protects your _wallet_ (app just turns off) but not the _experience_.

**Recommended fixes (pick one) — NOT yet done:**
1. **Cap upload size** in the FastAPI backend (reject files over ~10k–50k rows for the public demo). Best balance. Requires a code change in `aureviaforge-engine`.
2. **Sample data only** — public demo loads a built-in example dataset, no uploads. Zero risk.
3. **Demo on request** — uploads off the public version; do live walkthroughs instead.

For a public CV link, option 1 or 2 is strongly advised before sharing the link widely.

---

## 7. AureviaForge — technical summary

- **Frontend:** React + Vite
- **Backend:** FastAPI + SQLite + DuckDB
- **AI layer:** Groq (free, UAE-accessible), model `llama-3.3-70b-versatile`
- **What it does:** processes up to 100M transactions per run; 10 forensic tests (Benford 1st & 2nd digit, duplicate detection, threshold avoidance, round-number, gap & sequence, same-day anomalies, vendor concentration, statistical outliers, weekend & after-hours); ranks exceptions; case notes; CSV export; plain-language AI interrogation of the data.

---

## 8. Darvin & the Pulse — technical summary

- **Backend:** FastAPI + uvicorn
- **AI:** Groq (`llama-3.3-70b-versatile`) primary, Gemini fallback
- **Concept:** 3-agent adversarial tribunal — Darvin (Fraud Examiner / Prosecution), Ward (Defense Counsel), Athena (Chief Arbiter / Verdict). Findings are "put on trial" before reaching a report.
- **Status:** Beta. Pushed to GitHub (public). Demo not yet deployed. Could be hosted free on Render later.
- **API keys:** never commit them. `.gitignore` excludes `.env`. Keys read via `os.getenv()` only.

---

## 9. Maintenance reminders

- **Keep claims accurate** — "100 million transactions," the 10 tests, etc. should all be defensible if a technical interviewer probes.
- **Repo must stay public** for the free site to work. Never delete it.
- **Live-app button** depends on Railway staying active and the URL staying the same.
- Note: the "Available for work" badge that briefly existed in the footer has been **removed** — the footer is now big text + LinkedIn button + email icon only.

---

## 10. Optional upgrades (not done yet)

- **Custom domain** (~$10/yr), e.g. `akshayrajagopal.com`, pointed at GitHub Pages — biggest credibility upgrade; makes the link short and permanent.
- **Deploy Darvin** free on Render to make its demo link live.
- **Upload size cap / sample-data mode** for AureviaForge (see §6) — do before sharing widely.
- **Move AureviaForge to Render free tier** to drop the $5/mo Railway cost (tradeoff: free tier sleeps when idle, slow first load).

---

## 11. Quick command cheat-sheet

```bash
# Update the live portfolio
cd ~/Documents/akshay-portfolio
cp "$(ls -t ~/Downloads/*.html | head -1)" index.html
git add index.html
git commit -m "your message"
git push
# then wait ~90s and view in a Safari Private Window

# Undo local changes to index.html before committing
git checkout index.html

# See newest downloaded html (verify before copying)
ls -t ~/Downloads/*.html | head -1

# Live URLs
# Portfolio:   https://akshay-rajagopal-7.github.io/akshay-portfolio/
# Live app:    https://aureviaforge-engine-production.up.railway.app
```
