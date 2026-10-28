# Northwind Sales Analysis (SQL)

## What this is
I wanted to see where a food distributor's money comes from, who its key customers are, and where the risks are. This project answers eight business questions in SQL: revenue by category, top customers and countries, monthly trends, best-selling products, employee performance, late shipments, discounts and lapsed customers.

## Data
The Northwind sample database (a free, fictional company dataset from Microsoft) in its SQLite version. After I removed some synthetic rows that were added to the copy I used, it has 830 orders (July 2016 to May 2018), 2,155 order lines, 91 customers, 77 products and 9 employees across 7 linked tables. The notebook downloads and cleans it automatically, so you don't need to upload anything.

## How I did it
- Wrote the queries in SQLite and ran them from a Google Colab notebook (Python with sqlite3 and pandas)
- Joined up to three tables at a time (order lines, orders, customers, products, categories, employees, shippers)
- Used CTEs (including two chained together) and window functions (`LAG`, `RANK() OVER (PARTITION BY ...)`)
- Used `CASE WHEN` for the late-shipment and discount flags, and `LEFT JOIN` with `HAVING` to find lapsed customers
- Cleaned the data first: removed about 15,000 synthetic orders and 2 junk customer rows, and left out May 2018 from the trend since the month is incomplete

## What I found
- Beverages and Dairy are about 40% of revenue, and one product (Côte de Blaye) is about 53% of Beverages.
- The top 3 customers bring in about 25% of revenue and the top 10 about 45%. The USA and Germany together are about 38%.
- January to April 2018 revenue was about 121% higher than the same months of 2017.
- Peacock leads on total revenue (most orders), and Dodsworth has the highest revenue per order.
- 4.6% of shipped orders were late, and the difference between shippers isn't statistically significant (p of about 0.68).
- Discounted orders are about 24% bigger on average, but they also have more lines, so this doesn't show that discounts cause bigger orders.
- 2 customers never ordered and 9 haven't ordered in four months, including a top-10 customer (Mère Paillarde).

## What I'd recommend
Look after the biggest accounts and the Beverages line, contact lapsed high-value customers first, and test the effect of discounts more fairly (for example, order value per line) before changing any policy.

## Limitations
Northwind is a made-up company with a small number of orders, so small differences can be noise. The four-month cutoff for lapsed customers is simple and would be too strict for customers who only order once or twice a year.

## Tools
SQL (SQLite), Python (pandas, sqlite3), Google Colab
