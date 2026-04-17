# ServiceNow Cases Dashboard

Interactive dashboard for visualizing ServiceNow customer service case data. Built as a single self-contained HTML file — no server, no build step, no dependencies to install.

## Features

- **5 KPI cards** — Total cases, open/closed counts, avg response time, avg resolution time
- **7 interactive charts** — State, priority, product, assignment group, monthly trend, response time by priority, top contacts
- **5 multi-select filters** — Priority, State, Product, Assignment Group, Month (all support selecting multiple values)
- **3 tabs** — Overview, Monthly Breakdown, All Cases
- **CSV upload** — Drag-and-drop or click to load any ServiceNow case export
- **Dual header support** — Accepts both standard headers (`Opened`, `Number`, `State`, etc.) and ServiceNow API headers (`opened_at`, `number`, `state`, etc.)

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
3. Paste your GitHub Pages URL:
   ```
   https://YOUR_USERNAME.github.io/sn-cases-dashboard/
   ```
4. The dashboard will render as an interactive iframe inside your Zoom Doc

### Tips for Zoom Doc Embedding

- The embed will be fully interactive — filters, charts, and tabs all work inside the iframe
- You can resize the embed block by dragging its edges for a better view
- CSV upload works within the embed — drag a file onto the upload area
- For the best experience, make the embed block as wide as possible

---

## Updating the Dashboard Data

Since this dashboard loads data via CSV upload (no data is hardcoded), you don't need to redeploy to update data. Simply:

1. Export a fresh CSV from ServiceNow
2. Open the dashboard (or the Zoom Doc embed)
3. Click **📂 Load New CSV** and upload the new file

---

## Supported CSV Formats

The dashboard accepts CSVs with either header format:

**ServiceNow API headers:**
```
opened_at, number, contact, sys_created_by, priority, u_user_role, product, short_description, state, first_response_time, resolved_at, assignment_group
```

**Friendly headers:**
```
Opened, Number, Contact, Created by, Priority, User Role, Product, Short description, State, First Response Time, Resolved, Assignment group
```

---

## File Structure

```
sn-dashboard-ghpages/
├── index.html    ← The complete dashboard (single file, no dependencies)
└── README.md     ← This file
```
