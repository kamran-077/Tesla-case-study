# Tesla-case-study
This Project defines about complete analytics on Tesla through POWER BI and SQL analysis with following details ...
# Tesla Case Study: SQL + Power BI Analytics Project

An end-to-end data analytics project that cleans Tesla-style sales data, loads it into a **PostgreSQL** database, and visualizes customers, orders, and revenue in an interactive **Power BI** dashboard.

> **Note:** The dataset is a sample/synthetic dataset created for learning and portfolio purposes. It does not contain real Tesla customer data.

---

## Project Overview

The goal of this project is to analyze the sales performance of a Tesla-style business across vehicles and energy products, and to answer questions such as:

- How much revenue is generated, and how much is lost to refunds?
- Which product categories sell the most?
- What share of orders are delivered, cancelled, returned, or still pending?
- Which payment methods do customers prefer?
- How do customers differ by membership tier and region?

## Tools & Technologies

| Tool | Purpose |
|---|---|
| Python / Excel | Data cleaning |
| PostgreSQL | Database design and data loading |
| SQL | Table creation and querying |
| Power BI Desktop | Interactive dashboard |

## Dataset

Three cleaned CSV files (about 10,000 rows each), covering orders from **January 2023 to December 2025**.

| File | Rows | Description |
|---|---|---|
| `customers_cleaned.csv` | 10,000 | Customer ID, name, email, city, region, country, signup date, membership tier |
| `orders_cleaned.csv` | 10,000 | Order ID, customer, date, product category, quantity, unit price, status, payment method |
| `revenue_cleaned.csv` | ~9,700 | Payment ID, order, payment date, amount paid, payment status, refund amount |

**Product categories:** Model 3, Model S, Model X, Model Y, Powerwall, Solar Panel Kit, Supercharging Credits, Merchandise

**Membership tiers:** Standard, Insider, Referral Program, Unknown

**Order statuses:** Delivered, Shipped, Pending, Cancelled, Returned, Unknown

**Payment methods:** Cash, Financing, Lease, Credit Card

## Database Schema

The data is organized into three related tables in a database called `tesla_db`:

```
customers (customer_id PK)
    └── orders (order_id PK, customer_id FK)
            └── revenue (revenue_id PK, order_id FK)
```

The full `CREATE TABLE` statements and `\COPY` import commands are in [`Tesla_Postgres Queries.txt`](Tesla_Postgres%20Queries.txt).

## How to Reproduce

1. **Create the database** in PostgreSQL:
   ```sql
   CREATE DATABASE tesla_db;
   ```
2. **Create the tables** by running the `CREATE TABLE` statements from `Tesla_Postgres Queries.txt`.
3. **Load the data** with the `\COPY` commands. Update the file paths to match where you saved the CSVs on your machine.
4. **Open the dashboard**: open `tesla_casestudy_dashbord_post.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Windows). If the data source path has changed, go to *Transform data → Data source settings* and update it.

## Dashboard
<!-- ![Dashboard Preview](dashboard_preview.png) --><img width="1327" height="742" alt="dashboard_preview" src="https://github.com/user-attachments/assets/27a68de6-b405-454e-baa5-96c0233b6305" />


The Power BI report is in [`tesla_casestudy_dashbord_post/`](tesla_casestudy_dashbord_post/).

## Key Insights

- _Total revenue : 344.80M
- _Best-selling product category: supercharging Credits
- _Share of cancelled/returned orders: 25%
- _Preferred payment method: cash , credit card , financing , lease

## Repository Structure

```
├── customers_cleaned.csv
├── orders_cleaned.csv
├── revenue_cleaned.csv
├── Tesla_Postgres Queries.txt
├── tesla_casestudy_dashbord_post.pbix
└── README.md
```

## Author
**Kamran Shahid**
@kamran-077

---

*If you found this project useful, consider giving it a star.*
