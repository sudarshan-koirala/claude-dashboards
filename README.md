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

### Build Your First Dashboard

> Build a dashboard for Sunrise Bakery from the daily_sales table in Google Drive. I want to know how each of our three shops did from July to September 2026: total revenue, revenue per shop, weekly revenue trend per shop, and our top 5 products by units sold.

### Check the Query Behind Every Number

> Explain the query behind the Total Revenue number in simple words. What does it count, and what does it leave out?

### Refine It in Plain English

> Add a filter for location at the top, so I can look at one shop at a time.

> Add a chart that compares weekday and weekend revenue per shop, month by month.

### Find the Hidden Problem

> Harbor weekend revenue looks much lower in September. Compare average revenue per weekend day for Harbor in July, August and September, and show which products dropped the most.

> Add a stock panel from the inventory table. Highlight any product at or below its reorder level.

### Backup Prompts

> Make a simpler dashboard: 3 number cards (total revenue, best shop, best product) and one weekly revenue line per shop.

> The revenue column is revenue_eur and the date column is order_date.

> Show a line chart of Harbor revenue on Saturdays and Sundays only, by week, from July to September 2026.

> Which product grew the fastest at the Station shop after September 15?

> Refresh all charts and include data up to October 21, 2026.
