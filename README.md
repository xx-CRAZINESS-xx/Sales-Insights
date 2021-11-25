# SALES ANALYSIS

This is a Power BI dashboard of sales of a company from 2017-2020


## Screenshots

![Alt text](https://github.com/xx-CRAZINESS-xx/Sales-Insights/blob/main/Screenshot/Screenshot%201.png?raw=true)

![Alt text](https://github.com/xx-CRAZINESS-xx/Sales-Insights/blob/main/Screenshot/Screenshot%202.png?raw=true)


## Instructions

#### MySQL



- Follow step in this video to install MySQL on your local computer https://youtu.be/H0ZpCVhS6hw

- Create a new MySQL connection and import the data.
  Server ->  Data Import -> import from Self Contained File -> provide file location -> Start Import

#### Power BI

- Download and install Power BI from Microsoft Store

- Open Power Bi and select Get Data -> MySQL database -> connect

- Provide the localhost name and database name click OK

- Select all the tables and click load
## Data Analysis using MySQL

 1.   Show all customer records

    SELECT * FROM customers;

 2.  Show total number of customers

    SELECT COUNT(*) FROM customers;

 3.  Show transactions for Chennai market (market code for chennai is Mark001)

    SELECT * FROM transactions WHERE market_code='Mark001';

4.   Show distinct product codes that were sold in chennai

    SELECT DISTINCT product_code FROM transactions WHERE market_code='Mark001';

5.   Show transactions where currency is US dollars

    SELECT * FROM transactions WHERE currency="USD"

6.   Show transactions in 2020 join by date table

    SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020;

7.   Show total revenue for 2020

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020;

8.    Show total revenue for January 2020

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020 AND date.month_name="January" ;

9.   Show total revenue in year 2020 from Kochi (market code is Mark010)

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020 AND transactions.market_code="Mark010";
## Data Analysis using Power BI

 1.   Remove blank columns from markets
    = Table.SelectRows(sales_markets, each ([zone] <> ""))

 2.   Formula to create new sales amount column

    = Table.AddColumn(#"Filtered Rows", "new_sales_amount", each if [currency] = "USD" then [sales_amount]*75 else [sales_amount], type any)
    
    
