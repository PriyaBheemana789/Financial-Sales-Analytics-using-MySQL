**Financial Sales Analytics using MySQL**
**Project Overview**

Developed a complete SQL-based sales analytics solution for a retail business using MySQL.
The project focuses on analyzing customer sales, gross revenue, fiscal year performance, and quarterly trends by integrating multiple business tables and automating calculations using SQL functions and stored procedures.

**Business Objective**

Help business users answer questions like

How much revenue did a customer generate?
Which products generated the highest sales?
What are monthly and yearly sales?
What is sales performance by fiscal quarter?
Automate financial calculations without rewriting SQL.

**Database Tables**
dim_customer
dim_product
fact_sales_monthly
fact_gross_price
fact_manufacturing_cost
fact_forecast_monthly

**SQL Concepts Used**
✔ Inner Joins
✔ Aggregate Functions
✔ GROUP BY
✔ ORDER BY
✔ Stored Procedures
✔ User Defined Functions
✔ Date Functions
✔ Business Logic
✔ Financial Calculations
✔ Query Optimization

**Features**
**1. Fiscal Year Function**
Created reusable UDF
get_fiscal_year(date)
Automatically converts
2020-09-01
↓
FY2021

**2. Fiscal Quarter Function**
Created
get_fiscal_quarter(date)
Returns
Q1
Q2
Q3
Q4
based on custom company fiscal calendar.

**3. Customer Gross Sales Procedure**
Created stored procedure
get_monthly_gross_sales_for_customer(customer_code)
Returns
Fiscal Year
Total Gross Sales
for any customer.

**4. Sales Reporting**
Generated
Monthly Sales
Quarterly Sales
Yearly Sales
Product-wise Sales
Customer-wise Sales
Gross Revenue

**Sample Query**
SELECT
    s.date,
    p.product,
    s.sold_quantity,
    g.gross_price,
    ROUND(s.sold_quantity*g.gross_price,2) AS Gross_Sales
FROM fact_sales_monthly s
JOIN dim_product p
ON p.product_code=s.product_code
JOIN fact_gross_price g
ON g.product_code=s.product_code
AND g.fiscal_year=get_fiscal_year(s.date);

**Business Insights**
Automated fiscal year calculations using reusable SQL functions.
Reduced repetitive query writing through stored procedures.
Generated monthly, quarterly, and yearly sales reports.
Calculated customer gross sales based on historical pricing.
Enabled reusable reporting logic for financial analysis.
