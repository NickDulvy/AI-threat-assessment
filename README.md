# AI Threat Assessment Scoring Dashboard

This project provides a browser-based dashboard to score AI-generated threat justification tables against your rubric.

Project links:

- GitHub repository: [https://github.com/NickDulvy/AI-threat-assessment](https://github.com/NickDulvy/AI-threat-assessment)
- GitHub Pages app URL: [https://nickdulvy.github.io/AI-threat-assessment/threat_scoring_dashboard.html](https://nickdulvy.github.io/AI-threat-assessment/threat_scoring_dashboard.html)

Main app file:

- `threat_scoring_dashboard.html`

Example input file in this repo:

- `potamotrygon_yepezi_threat_assessment_table.csv`

## What the Dashboard Does

- Loads your assessment table from `.csv` or `.xlsx`.
- Walks through each row (Threat + Reason + Evidence) for scoring.
- Shows rubric guidance inline while you score.
- Autosaves your progress in browser local storage.
- Exports a final scored CSV in the same structure as the original sheet.

## Expected Sheet Structure

The dashboard is designed around these columns (matching your rubric workflow):

- `Threat`
- `Reason`
- `Evidence`
- `Strength of evidence`
- `Reason: Accuracy/Logic`
- `Reason: Relevance to the species`
- `Evidence: Accuracy`
- `Evidence: Relevance`
- `Strength: Accuracy`
- `Comments`

If your headers vary slightly, map columns manually in the dashboard.

## How To Use (Local)

1. Open `threat_scoring_dashboard.html` in your browser.
2. Upload your assessment file (`.csv` or `.xlsx`).
3. Select sheet (for Excel files) and map columns.
4. Click **Start Threat/Reason Walkthrough**.
5. Score each row and add comments where needed.
6. Click **Download Final Scored CSV** to export.
7. (Recommended) Click **Choose Save Folder**, select `01_CompletedAssessments`, then use:
   - **Save Partial** while assessment is in progress
   - **Save Complete** when finished

Output file name:

- `<original_filename>_scored.csv`

## Autosave Behavior

- Scores are autosaved while you work.
- Autosave is local to your browser/device.
- Reopening the same file/sheet structure restores prior progress.
- To fully reset, clear browser storage for the site.
- If you reopen a previously saved partial CSV, the dashboard reads existing score columns and resumes from the first incomplete row.

## Folder-Based Partial/Complete Saves

- Input queue folder: `00_ToBeAssessed`
- Output folder: `01_CompletedAssessments`
- Partial/complete saves write CSV files with timestamped names:
  - `<base>_PARTIAL_YYYYMMDD_HHMMSS.csv`
  - `<base>_COMPLETE_YYYYMMDD_HHMMSS.csv`
- Direct folder save uses the browser File System Access API (Chrome/Edge recommended).
- If folder-write is unavailable, use **Download Final Scored CSV** and place the file in `01_CompletedAssessments` manually.

## Recommended Local Serving

Opening the file directly works, but serving locally is more robust.

From this project folder:

```bash
python3 -m http.server 8080
```

Then open:

- [http://localhost:8080/threat_scoring_dashboard.html](http://localhost:8080/threat_scoring_dashboard.html)

## Deployment Options (GitHub First)

### Option A: GitHub Pages (recommended)

Best for easy team access with no backend.

1. Create a GitHub repository (or use an existing one).
2. Commit and push at least:
   - `threat_scoring_dashboard.html`
   - `README.md`
3. In GitHub: **Settings -> Pages**.
4. Under **Build and deployment**, choose:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main` (or `master`) and `/ (root)`
5. Save. GitHub will publish a URL like:
   - `https://<org-or-user>.github.io/<repo>/`
6. Share that URL with colleagues.

Notes:

- This is a static app; no server/database required.
- Each colleague's uploaded data and autosave stay in their own browser.

### Option B: GitHub + Netlify/Vercel

Useful if you want preview deployments and custom domain workflows.

- Connect repo to Netlify or Vercel.
- Set publish directory to repo root.
- Deploy as static site.

### Option C: Internal Hosting

If your institution has internal static hosting, upload the same files there.

## Data and Privacy Notes

- Uploaded spreadsheets are processed in-browser.
- No data is sent to your server by default.
- The dashboard currently loads SheetJS (`xlsx`) from a CDN.
  - For offline/air-gapped use, vendor `xlsx.full.min.js` locally and update the script reference.

## Suggested Next Enhancements

- Export `.xlsx` as well as `.csv`.
- Add a final "Overall assessment" section (Part II rubric prompts).
- Add reviewer name/date metadata in the export.
