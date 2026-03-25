# Investment Dashboard

A single-page investment tracking dashboard hosted on GitHub Pages. It reads data live from a Google Sheet and displays summary cards, allocation charts, and filterable tables for India and US investments.

**Live URL:** [https://arummani.github.io/investment-dashboard/](https://arummani.github.io/investment-dashboard/)

---

## How to Maintain This Dashboard

### Step 1 — Find your SHEET_ID

Open your Google Sheet in a browser. The URL looks like:

```
https://docs.google.com/spreadsheets/d/1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgVE2upms/edit#gid=0
```

The highlighted part between `/d/` and `/edit` is your **SHEET_ID**. Open `index.html` in any text editor and replace `YOUR_GOOGLE_SHEET_ID_HERE` near the top of the `<script>` block.

### Step 2 — Find your TAB_GID (gid for Table1)

Click on your **Table1** tab in Google Sheets. Look at the end of the browser URL for `#gid=1234567890`. That number is your **TAB_GID**. If Table1 is the first (or only) tab, it is usually `'0'`. Set `const TAB_GID = '0'` (or the actual number) in the script.

### Step 3 — Make the sheet publicly readable

In Google Sheets click **Share > Change to anyone with the link > set role to Viewer > Done**.

The dashboard reads data through a public Google API endpoint called "gviz" — it never writes to your sheet. Anyone who has your GitHub Pages URL can see your investment data, so avoid putting full account passwords or PIN numbers in the sheet.

### Step 4 — Deploy to GitHub Pages

1. Create a GitHub repository (can be private or public).
2. Commit `index.html` (with your SHEET_ID filled in) to the `main` branch.
3. Go to **Settings > Pages > Source > Deploy from branch > main /root > Save**.
4. GitHub will give you a URL like `https://your-username.github.io/your-repo/`. Bookmark it — that is your dashboard.

### Step 5 — Day-to-day usage

You **only ever touch the Google Sheet**. Add a new row for a new investment, edit amounts, update dates — then open (or refresh) your GitHub Pages URL. The dashboard re-reads live data on every load and on every click of the **Refresh** button.

**Expected column order in Table1** (row 1 = header, data from row 2):

`Company · Type · Account Number · Investment Amount · Country · Start Date · Maturity Date · Life Cover`

---

## Tech Stack

- **Tailwind CSS** (CDN) — styling
- **Chart.js** (CDN) — donut chart
- **Google Sheets gviz API** — live data endpoint
- Single `index.html` file, no build step required
