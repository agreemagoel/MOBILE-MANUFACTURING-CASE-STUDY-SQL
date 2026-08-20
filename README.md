# Cellphone Sales & Customer Analytics — SQL Case Study

A SQL-based analysis of cellphone sales transactions across a normalized fact-dimension schema (customers, manufacturers, models, locations). Solves 10 business questions — from customer geography and top-selling manufacturers to year-over-year spend trends and 3-year consistent top performers — using window functions (RANK/DENSE_RANK), CTEs, and self-joins.

## Business Scenario

A cellphone retailer's transactional database, `Cellphones Information`, tracks sales across manufacturers, models, customers, and locations. The goal is to answer a set of business questions around customer geography, manufacturer performance, and sales trends to support merchandising and customer-targeting decisions.

## Data Schema

The database follows a star schema with one fact table and four dimension tables:

| Table | Description |
|---|---|
| `Fact_Transactions` | One row per sale — model, customer, location, date, quantity, total price |
| `Dim_Manufacturer` | Manufacturer ID and name |
| `Dim_Model` | Model ID, name, unit price, linked manufacturer |
| `Dim_Customer` | Customer ID, name, email, phone |
| `Dim_Location` | Location ID, zip code, city, state, country |

## Business Questions Answered

1. States with customers who have purchased cellphones from 2005 to present
2. Top-buying US state for Samsung cellphones
3. Transaction count by model, zip code, and state
4. Cheapest cellphone available (with price)
5. Average price per model among the top 5 manufacturers by sales quantity
6. Customers with average 2009 spend above $500
7. Models that stayed in the top 5 by quantity across 2008, 2009, and 2010
8. 2nd-highest-selling manufacturer in 2009 and in 2010
9. Manufacturers that sold in 2010 but not in 2009
10. Top 100 customers by average spend/quantity per year, with year-over-year % change

## Techniques & Concepts Used

- Multi-table joins across a fact-dimension schema
- Window functions (`RANK`, `DENSE_RANK`) for top-N and ranking-by-group logic
- Self-joins for year-over-year comparisons
- Common Table Expressions (CTEs) for staged, readable query logic
- Aggregate functions with multi-level `GROUP BY` / `HAVING`
- Percentage-change calculations across time periods

## Tech Stack

- **SQL** (T-SQL / MS SQL Server)
- Schema created and queried locally in SQL Server Management Studio (SSMS)

## Repository Structure

```
├── schema.sql        # DDL — creates the 5-table schema
├── queries.sql        # Solutions to all 10 business questions
└── README.md
```

## How to Run

1. Execute `schema.sql` to create the database and tables.
2. Load or generate sample transaction data (see comments in `schema.sql`).
3. Run each query in `queries.sql` against the database — each is self-contained and mapped to a numbered business question.

## Key Takeaways

This project demonstrates applied SQL for business analytics: translating open-ended business questions into structured, efficient queries against a relational schema, with an emphasis on ranking, cohort/trend analysis, and multi-dimensional aggregation — the kind of query work used for customer, product, and merchant performance analysis in a retail or transactional business.

