# BigQuery Analytics Project

## About the project

A practical data analytics and data engineering project focused on working with Google BigQuery and cloud-based data warehousing.

The project explores the transition from local SQL databases to a serverless Data Warehouse environment, using a **Medallion Architecture** to organize data into Bronze, Silver, and Gold layers.

The project uses transactional, company, user, credit card, and product data to practice data ingestion, cleaning, transformation, business logic, and analytical queries.

## Data architecture

The project follows a Medallion Architecture with three logical layers implemented as BigQuery datasets:

### Bronze

The Bronze layer contains the raw data and external tables connected to files stored in Google Cloud Storage.

Main tables:

- `transactions_raw`
- `companies_raw`
- `american_users_raw`
- `european_users_raw`
- `credit_cards_raw`
- `products_raw`

### Silver

The Silver layer contains native BigQuery tables with cleaned and standardized data.

Main transformations include:

- Renaming columns
- Converting data types
- Handling invalid values with `SAFE_CAST`
- Handling null values
- Transforming product IDs into arrays
- Combining users from different regions
- Standardizing warehouse IDs

Main tables:

- `products_clean`
- `transactions_clean`
- `users_combined`
- `companies_clean`
- `credit_cards_clean`

### Gold

The Gold layer contains business-oriented views and tables prepared for analysis.

Main outputs:

- `v_marketing_kpis`
- `product_sales_ranking`

## Technologies

- Google BigQuery
- SQL
- Google Cloud Platform
- Google Cloud Storage
- Cloud Shell
- Gemini
- Git / GitHub

## Exercises

### Level 1 — Environment and Data Ingestion

The first level focused on setting up the BigQuery environment and implementing the Bronze layer.

Topics covered:

- Creating a Google Cloud project
- Creating Bronze, Silver, and Gold datasets
- Implementing a Medallion Architecture
- Creating external tables
- Working with CSV files stored in Google Cloud Storage
- Creating native BigQuery tables
- Comparing external and native tables
- Query cost analysis
- Using Dry Run
- Analytical queries using `CAST`, `EXTRACT`, `GROUP BY`, `ORDER BY`, and `LIMIT`

The project datasets were configured in the **EU region** as required by the exercise. :chatgpt-content-reference{index="0"}

### Level 2 — Data Cleaning and Transformation

The second level focused on preparing the data in the Silver layer.

Topics covered:

- Creating cleaned native tables
- Standardizing column names
- Data type conversion
- `SAFE_CAST`
- `IFNULL`
- `REPLACE`
- `SPLIT`
- `TRIM`
- `UNNEST`
- Working with `ARRAY` data
- Combining datasets using `UNION ALL`

One of the main transformations was converting the `product_ids` field from a string containing multiple product IDs into an `ARRAY<INT64>`, making the data easier to analyze later.

### Level 3 — Data Analysis and Business Logic

The third level focused on preparing business-ready information in the Gold layer.

Topics covered:

- Creating SQL views with `CREATE VIEW`
- Joining companies and transactions
- Calculating average transaction values with `AVG`
- Grouping data with `GROUP BY`
- Creating business classifications with `CASE`
- Flattening product arrays using `UNNEST`
- Counting product sales
- Using `LEFT JOIN` to preserve products with zero sales
- Exporting analytical results to CSV / Google Sheets

The `product_sales_ranking` table contains the complete product catalog and the number of times each product appears in transactions, including products with zero sales. :chatgpt-content-reference{index="1"}

## Key BigQuery and SQL Concepts

- Medallion Architecture
- Data Warehousing
- External vs. native tables
- Serverless Data Warehouse
- Query cost optimization
- Dry Run
- Data cleaning
- Data type conversion
- `SAFE_CAST`
- `IFNULL`
- `SPLIT`
- `UNNEST`
- `ARRAY`
- `UNION ALL`
- `JOIN`
- `LEFT JOIN`
- `GROUP BY`
- `CASE`
- SQL Views
- Analytical queries

## Cost Analysis

An important part of the project was understanding how BigQuery processes and charges for queries.

The project compared external and native tables and evaluated the amount of data processed and billed when querying each type of table.

This helped demonstrate the importance of considering query design, data storage, and cost when working with cloud-based data warehouses.

## Project Structure

```text
sprint3-bigquery-analytics/
│
├── README.md
│
├── sql/
│   ├── 01_architecture.sql
│   ├── 02_bronze_external_tables.sql
│   ├── 03_silver_transformations.sql
│   └── 04_gold_analysis.sql
│
└── screenshots/
    ├── architecture.png
    ├── bronze_tables.png
    ├── silver_tables.png
    ├── marketing_kpis.png
    └── product_ranking.png
