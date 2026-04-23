# ServiceNow Cases Dashboard

Interactive dashboard for visualizing ServiceNow customer service case data and SLA performance. Built as a single self-contained HTML file — no server, no build step, no dependencies to install.

## Features

- **5 KPI cards** — Total cases, open/closed counts, avg response time, avg resolution time
- **7 interactive charts** — State, priority, product, assignment group, monthly trend, response time by priority, top contacts
- **5 multi-select filters** — Priority, State, Product, Assignment Group, Month (all support selecting multiple values)
- **4 tabs** — Overview, SLA Performance, Monthly Breakdown, All Cases
- **Dual file upload** — CSV for case data, Excel for SLA reports
- **Dual header support** — Accepts both standard headers (`Opened`, `Number`, `State`, etc.) and ServiceNow API headers (`opened_at`, `number`, `state`, etc.)

### SLA Performance Tab
- Parses monthly SLA Excel files with "First Response SLA" and "Resolve-Workaround SLA" sheets
- Displays SLA KPIs (met/breached counts and percentages) for both First Response and Workaround SLAs
- Monthly SLA % trend chart showing performance over time
- SLA breakdown by priority (stacked bar charts)
- Detailed SLA records table with ticket-level data
- SLA data is displayed independently of CSV case data — month filter applies to both

---

## Supported File Formats

### Case CSV
The dashboard accepts CSVs with either header format:

**ServiceNow API headers:**
```
opened_at, number, contact, sys_created_by, priority, u_user_role, product, short_description, state, first_response_time, resolved_at, assignment_group
```

**Friendly headers:**
```
Opened, Number, Contact, Created by, Priority, User Role, Product, Short description, State, First Response Time, Resolved, Assignment group
```

### SLA Excel Files
Monthly SLA reports (.xlsx) with two sheets:
- **First Response SLA** — Contains first response SLA metrics, summary, and ticket-level detail
- **Resolve-Workaround SLA** — Contains workaround/resolve SLA metrics, summary, and ticket-level detail

Each sheet follows this structure:
- Row 2: Customer name (col C)
- Row 3: Month (col C, as date)
- Row 4: SLA Metric name (col C)
- Row 7: Total Cases (col B, format: "Total Cases: \n<count>")
- Row 11: SLA Result (col B, format: "SLA Result: \n<pct>%")
- Row 14: Passed count (col A: "Passed", col B: count)
- Row 15: Failed count (col A: "Failed", col B: count)
- Row 17: Column headers (Number, Priority, User Role, etc.)
- Row 18+: Ticket-level SLA detail records

---

## Deploy to GitHub Pages

### Step 1: Create a GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Name it something like `sn-cases-dashboard`
3. Set visibility to **Private** (recommended for sensitive data) or Public
4. Click **Create repository**

### Step 2: Push the Files

```bash
cd sn-dashboard-ghpages
git init
git add .
git commit -m "Initial dashboard deployment"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/sn-cases-dashboard.git
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select **Deploy from a branch**
3. Set branch to `main` and folder to `/ (root)`
4. Click **Save**
5. Wait 1–2 minutes for deployment

Your dashboard will be live at:
```
https://YOUR_USERNAME.github.io/sn-cases-dashboard/
```

> **Note:** If the repo is private, only you (and collaborators) can access the Pages site. GitHub Pages for private repos requires a GitHub Pro, Team, or Enterprise plan.

---

## Embed in a Zoom Doc

Once your dashboard is live on GitHub Pages, you can embed it in a Zoom Doc:

1. Open your Zoom Doc
2. Type `/embed` or click the **+** menu and select **Embed**
3. Paste your GitHub Pages URL
4. The dashboard will render as an interactive iframe inside your Zoom Doc

---

## Updating the Dashboard Data

Since this dashboard loads data via file upload (no data is hardcoded), you don't need to redeploy to update data. Simply:

1. Export a fresh CSV from ServiceNow
2. Open the dashboard (or the Zoom Doc embed)
3. Click **📂 Load New Data** and upload new files

---

## File Structure

```
sn-dashboard-ghpages/
├── index.html    ← The complete dashboard (single file, no dependencies)
└── README.md     ← This file
```
