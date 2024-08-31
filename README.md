# Sales Insights Data Analysis Project 🛰

## Introduction 🙋🏻‍♂️
* **Atliq Hardware** is a company which supplies computer hardware and peripherals to various clients such as excel stores, nomad stores, Surge stores etc. across India. 
* Atliq hardware has a head office in Delhi and they have many regional offices across India, 
* The sales director is having a problems tracking sales in this dynamically growing market. The sales director is also having issues trying to obtain insights of his business. Overall, the sales of the company seem to be declining.

## About the Project:
* Performed India based hardware company Sales Insights - A Data Analysis project.

* Developed ETL mappings using SQL to extract the data from unstructured data and transformed it to the staging area to conduct data cleaning and designed star schema data model on Tableau.

* Developed a Power BI dashboard to perform analysis, producing quantitative visualizations to draw valuable insights based on different parameters affecting company's performance year on year and to further provide them business solutions and changes.

## Technology Used 🔧
* Microsoft Power BI 📈
* MySQL Workbench CE 🐬

## Project Planning 👨🏻‍✈️
* Project planning was done using a project management tool called **AIMS Grid**.
![Aims Grid](https://raw.githubusercontent.com/devschow/Sales-Insights-Data-Analysis/main/AIMS%20Grid.jpg)

## The ETL Workflow:
![ETL Workflow](https://content.altexsoft.com/media/2021/03/the-etl-workflow.png.webp)

## Data Modeling:
Star Schema:
![Data Model](https://raw.githubusercontent.com/devschow/Sales-Insights-Data-Analysis/main/Data_Model.jpg)

Main table: 
- sales transactions 

TABLES CONNECTED
- sales customers > connected by “customer_code” column;
- sales date> connected by “date” column;
- sales products > connected by “product_code” column;
- sales markets > connected by “market_code” column.

Measures created: 
- “Revenue” and “Sales Qty” measures to get the sum of each column instantly in the dashboard.
- "Revenue LY" mesures the revenue generated last year 

# 1) Data Analysis Using SQL:

- The dataset was examined using MySQL to unlock any trends, features, or other potential areas of interest.
- This method is intended to help generate a broader picture rather than show every piece of information that a dataset contains.

## Show all customer records

SELECT * FROM customers;

## Show total number of customers

SELECT count(*) FROM customers;

## Show transactions for Chennai market (market code for chennai is Mark001)

SELECT * FROM transactions where market_code='Mark001';

## Show distrinct product codes that were sold in chennai

SELECT distinct product_code FROM transactions where market_code='Mark001';

## Show transactions where currency is US dollars

SELECT * from transactions where currency="USD"

## Show transactions in 2020 join by date table

SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

## Show total revenue in year 2020,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

## Show total revenue in year 2020, January Month,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date 
where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

## Show total revenue in year 2020 in Chennai

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

# 2) Data Analysis Using Power BI:

## Formula to create norm_amount column:

= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*82 else [sales_amount], type any)

## Data Visualization 🖼
* **Dashboard 1:**
![Dashboard_1](https://raw.githubusercontent.com/devschow/Sales-Insights-Data-Analysis/main/Dashboard_1.jpg)

* **Dashboard 2:**
![Dashboard_2](https://raw.githubusercontent.com/devschow/Sales-Insights-Data-Analysis/main/Dashboard_2.jpg)

The dashboard displays all the key sales-related data, including 
* Revenue, sales quantity, revenue and sales by market 
* Revenue trend, Top 5 clients, and Top 5 products.

The sales director can quickly and easily get a deeper understanding of the sales to boost his decision-making by filtering the dashboard by YEAR and MONTH within the observation period.

## 🔗 Let's Connect!
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/devarshi-choudhury-367aa11b0/)

