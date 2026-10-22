# Claude Dashboards

These are the tables for Claude dashboard data for my YouTube channel.

## Files

| File | Description |
|------|-------------|
| `sunrise_daily_sales_october_update.csv` | Daily sales data — October update |
| `sunrise_daily_sales.csv` | Daily sales data — Q3 |
| `sunrise_inventory.csv` | Inventory data |

---

## Demo Prompts and Recording Prep

Verified as of October 22, 2026

### Recording Order

1. Databricks session: Step 2 upload, then pause. Record Step 8 INSERT later.
2. Claude settings session: Step 3 connector.
3. Claude main chat: Steps 4, 5, 6, 7, 9, 10 in one chat.
4. Back to Databricks: run the October INSERT (Step 8), then refresh the dashboard in Claude.
5. Hook LAST, over the finished dashboard.

---

### Step 4 — Build Your First Dashboard

**Prompt:**
> Build a dashboard for Sunrise Bakery from the daily_sales table in Databricks. I want to know how each of our three shops did from July to September 2026: total revenue, revenue per shop, weekly revenue trend per shop, and our top 5 products by units sold.

---

### Step 5 — Check the Query Behind Every Number

**Follow-up:**
> Explain the query behind the Total Revenue number in simple words. What does it count, and what does it leave out?

---

### Step 6 — Refine It in Plain English

**Follow-up:**
> Add a filter for location at the top, so I can look at one shop at a time.

**Follow-up:**
> Add a chart that compares weekday and weekend revenue per shop, month by month.

---

### Step 7 — Find the Hidden Problem

**Follow-up:**
> Harbor weekend revenue looks much lower in September. Compare average revenue per weekend day for Harbor in July, August and September, and show which products dropped the most.

**Follow-up:**
> Add a stock panel from the inventory table. Highlight any product at or below its reorder level.

---

### Backup Prompts

**If the first dashboard is too busy:**
> Make a simpler dashboard: 3 number cards (total revenue, best shop, best product) and one weekly revenue line per shop. Data: the daily_sales table in [catalog].[schema].

**If Claude picks the wrong table:**
> Use only the table [catalog].[schema].daily_sales. The revenue column is revenue_eur and the date column is order_date.

**If the weekend drop is not obvious:**
> Show a line chart of Harbor revenue on Saturdays and Sundays only, by week, from July to September 2026.

**Second discovery (positive):**
> Which product grew the fastest at the Station shop after September 15?

**If refresh does not show October:**
> Refresh all charts and include data up to October 21, 2026.

---

### Expected Results (verified in code)

- **Total Q3 revenue:** ~EUR 318,181
- **By shop:** Main Street EUR 121,699 | Station EUR 98,553 | Harbor EUR 97,929
- **Harbor revenue per weekend day:** July ~EUR 1,386 | August ~EUR 1,347 | September ~EUR 718 (~48% lower)
- **Harbor weekday revenue:** stays flat (~EUR 21,000–23,000/month)
- **Station after Sep 15:** Pumpkin Spice Latte is top product (1,330 units vs 787 for Cappuccino)
- **Inventory:** Almond Croissant at Harbor has 0 stock. Pumpkin Spice Latte at Station is below reorder level (35 vs 60)
- **October update:** adds 504 rows (Oct 1–21), ~EUR 82,208. Harbor weekend dip continues until Oct 3 (~EUR 755), then recovers to ~EUR 1,370–1,480/weekend day

---

### Setup Before Recording

#### Files

- `sunrise_daily_sales.csv` — 1,980 rows, Jul 1–Sep 30, 2026
- `sunrise_inventory.csv` — 24 rows, stock count on Oct 14
- `sunrise_daily_sales_october_update.csv` — 504 rows, Oct 1–21, for the live demo
- `sunrise_databricks_setup.sql` — table names and the October INSERT

> Note: the sales file is larger than the usual 20–100 rows on purpose. A trend chart needs daily data.

#### Settings

- Claude plan: Pro or higher. Check that **Output > Dashboards** shows in the message box.
- Databricks Free Edition workspace with Unity Catalog. Upload both Q3 files and the inventory file.
- Upload the October file as a separate table `daily_sales_october_staging`. **Do NOT insert it yet.**
- Add the Databricks custom connector in Claude: **Settings > Connectors > Add custom connector**.
  - Server URL format: `https://[your-workspace-host]/api/2.0/mcp/sql` (managed SQL server).
  - _Confirm on recording day: the exact managed MCP URL and that OAuth sign-in works on Free Edition. If it does not, use a BigQuery sandbox (FREE) with the same CSVs and the BigQuery connector._
- Run one test dashboard off camera, then delete it, so the connector is warm.

#### Apps Open

- Browser tab 1: claude.ai (new chat, Output menu visible)
- Browser tab 2: Databricks SQL editor with `sunrise_databricks_setup.sql` loaded
- Browser tab 3: support.claude.com Dashboards article (for Step 1)

#### Screen Recording Tips

- Dashboard builds take time. Record in real time, then speed up 4×–8× in edit.
- Zoom in when you click a number to show the query. This is the key trust moment.
- Hide your workspace host name and any tokens during the connector step (blur in edit).
- Use browser zoom 110% so charts read well on mobile.
- Results vary run to run. Use the Expected Results above to check numbers before you narrate them.
