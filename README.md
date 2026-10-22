# Claude Dashboards

These are the tables for Claude dashboard data for my YouTube channel.

## Files

| File | Description |
|------|-------------|
| `sunrise_daily_sales_october_update.csv` | Daily sales data — October update |
| `sunrise_daily_sales.csv` | Daily sales data — Q3 |
| `sunrise_inventory.csv` | Inventory data |

---

## Demo Prompts

### Step 4 — Build Your First Dashboard

> Build a dashboard for Sunrise Bakery from the daily_sales table in Google Drive. I want to know how each of our three shops did from July to September 2026: total revenue, revenue per shop, weekly revenue trend per shop, and our top 5 products by units sold.

### Step 5 — Check the Query Behind Every Number

> Explain the query behind the Total Revenue number in simple words. What does it count, and what does it leave out?

### Step 6 — Refine It in Plain English

> Add a filter for location at the top, so I can look at one shop at a time.

> Add a chart that compares weekday and weekend revenue per shop, month by month.

### Step 7 — Find the Hidden Problem

> Harbor weekend revenue looks much lower in September. Compare average revenue per weekend day for Harbor in July, August and September, and show which products dropped the most.

> Add a stock panel from the inventory table. Highlight any product at or below its reorder level.

### Backup Prompts

> Make a simpler dashboard: 3 number cards (total revenue, best shop, best product) and one weekly revenue line per shop.

> The revenue column is revenue_eur and the date column is order_date.

> Show a line chart of Harbor revenue on Saturdays and Sundays only, by week, from July to September 2026.

> Which product grew the fastest at the Station shop after September 15?

> Refresh all charts and include data up to October 21, 2026.

---

## Expected Results

- **Total Q3 revenue:** ~EUR 318,181
- **By shop:** Main Street EUR 121,699 | Station EUR 98,553 | Harbor EUR 97,929
- **Harbor revenue per weekend day:** July ~EUR 1,386 | August ~EUR 1,347 | September ~EUR 718 (~48% lower)
- **Harbor weekday revenue:** stays flat (~EUR 21,000–23,000/month)
- **Station after Sep 15:** Pumpkin Spice Latte is top product (1,330 units vs 787 for Cappuccino)
- **Inventory:** Almond Croissant at Harbor has 0 stock. Pumpkin Spice Latte at Station is below reorder level (35 vs 60)
- **October update:** adds 504 rows (Oct 1–21), ~EUR 82,208. Harbor weekend dip continues until Oct 3 (~EUR 755), then recovers to ~EUR 1,370–1,480/weekend day
