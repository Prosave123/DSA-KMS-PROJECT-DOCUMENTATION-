# DSA-KMS-PROJECT-DOCUMENTATION
My first portfolio building where i discussed the dsa (kms) project that was given to me

## PROJECT TPOIC: Kultra Mega Stores Inventory

## PROJECT OVERVIEW:
This report breaks down KMS's performance based on sales, customers, and shipping. It’s grouped into three parts: Sales Analysis, Customer Analysis, and Shipping Analysis. Each part answers important questions to help the company find ways to make more money, spend less, and serve customers better.

### Data Source
The analysis in this project draws from two key datasets—“KMS SQL Case Study.csv” and “Orders_Status.csv”—which were obtained through the DSA LMS Dashboard. These datasets serve as the foundation for uncovering insights into sales performance, customer behavior, and order management.

### TOOL USED
- SQL Server(Utilized for querying and data analysis) [Download here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

### Data cleaning and Preparation
During the initial phase of data preparation, the following steps are carried out:  
1. Loading and inspecting the dataset  
2. Identifying and addressing missing values  
3. Cleaning and formatting the data for analysis  

### Exploratory Data Analysis  
- EDA involved examining the dataset to answer key questions such as:
  - Which product category had the highest sales?
  - What are the Top 3 and Bottom 3 regions in terms of sales?
  - What were the total sales of appliances in Ontario?
  - Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
  - KMS incurred the most shipping cost using which shipping method?
  - Who are the most valuable customers, and what products or services do they typicall purchase?
  - Which small business customer had the highest sales?
  - Which Corporate Customer placed the most number of orders in 2009 – 2012?
  - Which consumer customer was the most profitable one?
  - Which customer returned items, and what segment do they belong to?
  - If the delivery truck is the most economical but the slowest shipping method and
Express Air is the fastest but the most expensive one, do you think the company
appropriately spent shipping costs based on the Order Priority? Explain your answer

### Data Analysis  
This section includes basic code snippets, SQL queries, I used during the analysis process.

### SQL QUERIES AND ANSWERS 
- To get Which product category had the highest sales, run the below query.
  - The result given is "Technology Category"

  ```` Sql
   SELECT 
    Product_category, 
    SUM(Sales) AS Total_Sales
   FROM 
    [dbo].[KMS Sql Case Study]
  GROUP BY 
    Product_category
  ORDER BY 
    Total_Sales DESC
  ````

- To get the Top 3 and Bottom 3 regions in terms of sales, run the below query.
  - Top 3 region are "West, Ontario, Prarie"
  - Bottom 3 region are "Nunavut, Northwest Territories, Yukon"

```` sql
   SELECT TOP 3
	Region, sum(Sales) as total_sales
FROM [dbo].[KMS Sql Case Study]
GROUP BY Region
order by total_sales desc


SELECT TOP 3
	Region, sum(Sales) as total_sales
FROM [dbo].[KMS Sql Case Study]
GROUP BY Region
order by total_sales ASC
````

- To get the total sales of appliances in Ontario, run the below query.
  - The result given is "202346.840"

```` Sql
SELECT 
	Region, sum(Sales)as total_sales , Product_Sub_Category
FROM [dbo].[KMS Sql Case Study]
WHERE REGION = 'ONTARIO'and Product_Sub_Category='Appliances'
GROUP BY Region,Product_Sub_Category
order by total_sales
````

- KMS incurred the most shipping cost using which shipping method, run the below query.
  - The result given is "Delivery Truck"

```` Sql
  select 
ship_mode,sum (shipping_cost)as total_cost
from [dbo].[KMS Sql Case Study]
group by ship_mode
order by total_cost desc
````

- To get the most valuable customers, and the products or services they typicall purchase, run the below query.

```` sql
  select top 10
Customer_Name,product_Name,sum(Profit) as total_profit
from [dbo].[KMS Sql Case Study]
group by Customer_Name, product_Name
order by total_profit desc
````
- The result given:
  - Top Valuable Customers and Their Most Purchased Products
    
| Customer Name       | Most Profitable Product                                                                          | Total Profit |
|---------------------|--------------------------------------------------------------------------------------------------|--------------|
| Emily Phan          | Polycom ViewStation™ ISDN Videoconferencing Unit                                                 | 27,221.00    |
| Clytie Kelty        | Canon PC940 Copier                                                                               | 15,601.00    |
| Andy Reiter         | Polycom ViaVideo™ Desktop Video Communications Unit                                              | 14,440.00    |
| Deborah Brumfield   | Hewlett Packard LaserJet 3310 Copier                                                             | 13,340.00    |
| Karen Carlisle      | Canon Image Class D660 Copier                                                                    | 12,749.00    |
| Rick Wilson         | HP Business Color Inkjet 3000 [N, DTN] Series Printers                                           | 12,607.00    |
| Raymond Book        | Hewlett Packard LaserJet 3310 Copier                                                             | 11,984.00    |
| Logan Haushalter    | Hewlett Packard LaserJet 3310 Copier                                                             | 11,630.00    |
| Nick Crebassa       | HP Business Color Inkjet 3000 [N, DTN] Series Printers                                           | 11,562.00    |
| John Stevenson      | Fellowes PB500 Electric Punch Plastic Comb Binding Machine with Manual Bind                      | 11,535.00    |
