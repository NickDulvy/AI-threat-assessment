# AI Threat Assessment Dashboard

Dashboard URL:

- [https://nickdulvy.github.io/AI-threat-assessment/threat_scoring_dashboard.html](https://nickdulvy.github.io/AI-threat-assessment/threat_scoring_dashboard.html)

Preferred browser:

- **Google Chrome** (recommended) or **Microsoft Edge**

## Quick Start (New User)

1. Open the dashboard URL above.
2. In **Load from GitHub repo folder**, choose:
   - `00_ToBeAssessed` for a new assessment, or
   - `01_PartiallyCompleteAssessments` to continue a partial assessment.
3. Click **Refresh Repo Files**.
4. Select a spreadsheet and click **Load Selected Repo File**.
5. Confirm column mapping, then click **Start Threat/Reason Walkthrough**.
6. Score each row.

## Saving Back to GitHub

1. Paste a GitHub Personal Access Token into **GitHub token (required for saving)**.
2. Click:
   - **Save Partial to GitHub** to save into `01_PartiallyCompleteAssessments`, or
   - **Save Complete to GitHub** to save into `02_CompletedAssessments`.

Saved filenames are datestamped:

- `<base>_PARTIAL_yymmdd_hhmm.csv`
- `<base>_COMPLETE_yymmdd_hhmm.csv`
- If a filename already exists, the dashboard auto-creates a unique name (e.g., `_02`, `_03`) so existing assessment files are never overwritten.

## Token Permissions

Your token must allow writing to this repository.

- Classic token: `repo` scope
- Fine-grained token: repository contents read/write permission for this repo
