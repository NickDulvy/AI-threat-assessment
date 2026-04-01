# Threat Scoring Dashboard: Local Use and Deployment

## Files

- `threat_scoring_dashboard.html` - single-file dashboard app
- Input: your threat table CSV/XLSX
- Output: downloadable `*_scored.csv` with your original columns plus rubric scores

## Local Use

1. Open `threat_scoring_dashboard.html` in a browser.
2. Load your CSV/XLSX.
3. Map columns (Threat, Reason, Evidence, optional Strength of evidence).
4. Start scoring.
5. Download the final scored CSV.

Autosave behavior:

- Scores autosave in browser local storage as you work.
- If you reopen the same file/sheet structure in the same browser, prior scores are restored.

## Run via Local Web Server (recommended)

From this project directory:

```bash
python3 -m http.server 8080
```

Then open:

- [http://localhost:8080/threat_scoring_dashboard.html](http://localhost:8080/threat_scoring_dashboard.html)

## Deploy for Colleagues (Static Hosting)

This app is a static HTML file, so any static host works:

- GitHub Pages
- Netlify
- Vercel (static)
- Institutional static web server

Upload at least:

- `threat_scoring_dashboard.html`

Notes:

- Colleagues' uploads and autosaves stay in their own browser (no server database required).
- The dashboard uses the SheetJS CDN script (`xlsx`) to read spreadsheets. If internet-restricted, replace CDN usage with a locally hosted `xlsx.full.min.js`.
