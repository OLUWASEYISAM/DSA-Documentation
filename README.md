# DSA CAPSTONE PROJECT: Kultra Mega Stores Inventory

Capstone Project for Data Analysis course with Digital Skillup Africa, Incubator Hub

Project will be executed using SQL to get insights to the data given for the project.

## PROJECT TOPIC: BUSINESS INTELLIGENCE ANALYSIS OF ORDER DATA IN KULTRA MEGA STORES (KMS) (2009 - 2012)

### Project Overview: 
KultraMega Stores (KMS), headquartered in Lagos, specialises in Office supplies and furniture. Its customer base includes individual consumers, small businesses (retail), and large corporate clients (wholesale) across Lagos, Nigeria. 
As a Business Intelligence Analyst to support the Abuja division of KMS. The Business Manager has shared an Excel file containing order data from 2009 to 
2012 and has requested that I analyze the data and present my key insights and findings. 

### Table of Content
1. Project Topic
2. Project Overview
3. Data Source
4. Tools used
5. Data Cleaning and Preparation
6. Exploratory Data Analysis (EDA)
 - Case Scenario 1
 - Case Scenario 2
7. Data Analysis (SQL Queries)
 
### Data Source
Data used for this project is a Primary data as it was shared directly from the Business Manager. 

### Tools Used
- Microsoft Excel
  - For Data Collection
  - For Data cleaning
    1. By Manipulation 
    2. By Data Munching.  
- SQL Server (For Querying and Analysis)
- MS Power Point (For Presentation)

### Data Cleaning and Preparation
In the initial phase of the Data cleaning, and preparations, we performed the following actions;
1. Data loading and Inspection: Checking for Missing data using COUNTBLANK functions and Filters, It was discovered that Product base Margin column has 63 empty cells/Missing data.
2. Handling missing variables: Missing data under the Product base Margin were handled using backward fill.
3. Data cleaning and formatting: We then do the needed formatting for Numbers, Dates and texts so as to prepare Data for Analysis.

### Exploratory Data Analysis (EDA)
EDA involved the exploring of the data to answer some questions about the data such as

#### Case Scenario 1
1. Which product category had the highest sales? 
- Ans: Technology category had the highes sales with a Total sales of 5984248.18.
  - Technology:       5984248.18199999
  - Furniture:	      5178590.54199999
  - Office Supplies:	3752762.09999999

2. What are the Top 3 and Bottom 3 regions in terms of sales? 
- Top 3 Regios in term of Sales:
  - West	  3597549.2755
  - Ontario	3063212.4795
  - Prarie	2837304.6015

- Bottom 3 Regios in term of Sales:
  - Nunavut	116376.4835
  - Northwest Territories	800847.3295
  - Yukon	975867.370999999

3. What were the total sales of appliances in Ontario?
- Ans: Total sales of appliances in Ontario is 3063212.48

4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers.
- Revenue made from Bottom 10 Customers
  - Jeremy Farry	      85.72
  - Natalie DeCherney	  125.9
  - Nicole Fjeld	      153.03
  - Katrina Edelman	    180.76
  - Dorothy Dickinson	  198.08
  - Christine Kargatis  293.22
  - Eric Murdock	      343.328
  - Chris McAfee	      350.18
  - Rick Huthwaite	    415.82
  - Mark Hamilton	      450.99

- Advice: 
  - Identify and segment low-spending customers by behavior, demographics, and purchase history.
  - Deploy targeted promotions, discounts, or bundles based on their preferences and past activities.
  - Introduce incentives, points cashback, referral bonuses, to encourage repeat purchases.
  - Improve customer experience by ensuring ease of navigation, payment and support.
  - Use SMS, email, or social media to re-engage inactive or low engagement customers.
  - Take feedbacks and collect insights indirectly on why purchases are low.

5. Shipping method with the most shipping cost
- Ans: The shipping method with the highest shipping cost is Delivery Truck with a total shipping cost of 51971.94
  - Delivery Truck	51971.9399999998
  - Regular Air	    48008.1899999997
  - Express Air	    7850.90999999997


#### Case Scenario 2
6. Who are the most Valuable customers, and what products or services do they typically purchase?
- Ans: The 6 (Six) most valuable customers are "Emily Phan", "Deborah Brumfield", "Dennis Kane", "Jasper Cacioppo", "Clytie Kelty" and "Raymond Book". They all purchase products in the Technology category.

- Revenue from Top 10 Customers to determine Most valuable customers and Product category they typically purchase
    - Emily Phan	      110481.968	Technology
    - Deborah Brumfield	76795.7955	Technology
    - Dennis Kane	      60434.6405	Technology
    - Jasper Cacioppo	  57739.27	  Technology
    - Clytie Kelty	    54454.95	  Technology
    - Raymond Book	    53450.78	  Technology
    - Lisa DeCherney	  52477.37	  Furniture
    - Alejandro Grove	  51696.02	  Office Supplies
    - Grant Carroll	    50837.27	  Office Supplies
    - Roy Skaria	      50177.24	  Furniture

7. Which small business customer had the highest sales?
- Ans: Small business customer with the highest sales was "Dennis Kane" with 75967.59 amount of sales.

8. Which Corporate Customer placed the most number of orders in 2009 – 2012?
- Ans: Corporate Customer that placed the most number of orders in 2009 – 2012 was "Adam Hart" with 27 orders placed.

9. Which consumer customer was the most profitable one?
- Ans: Most profitable Consumer customer was "Emily Phan" with 34005.44 profits made.

10. If the delivery truck is the most economical but the slowest shipping method and 
Express Air is the fastest but the most expensive one, do you think the company 
appropriately spent shipping costs based on the Order Priority? Explain your answer
- Ans: The company appropriately spent shipping costs based on the Order Priority
- Explanation: Orders that requires immediate and prompt delivery to customers were attended to using Express Air as shipping method since it is the fastest method. While Data gathered revealed that percentage shipping cost to sales made using Express Air delivery mode (0.66%) is even slightly lower compared percentage shipping cost to sales made using Delivery Truck mode (0.83%). This implies that despite Express Air mode being more expensive than Delivery Truck mode, the sales made from goods ordered by customers will cover for the shipping expenses.

 - Comparing Sales made from Delivery Truck and Express Air and Percentage of the shipping cost to Sales made. 
  - Ship Mode       Shipping cost     Sales             Percentage shipping cost to sales
  - Delivery Truck	51971.9399999998	6224878.71799999	0.834906868943753
  - Express Air	    7850.90999999997	1184418.897	      0.662849100084897

### Data Analysis
This are the lines of code or queries used in SQL to perform the analysis 

``` SQL
---Importing Data and View
select * from dbo.KMS

--------ANALYSIS---------
--1. Product Category with the Highest sales
select [Product Category], SUM(Sales) as [Total Sales]
from KMS
group by [Product Category]
order by [Total Sales] desc

--2a. Top 3 regions in terms of Sales
select top 3 Region, SUM(Sales) AS Sales
		from KMS
GROUP BY Region
Order by Sales desc

--2b. Bottom 3 regions in terms of Sales
select top 3 Region, SUM(Sales) AS Sales
		from KMS
GROUP BY Region
Order by Sales asc

--3. Total Sales of Appliances in Ontario
select Region, SUM(Sales) AS Sales 
	from KMS
where Region = 'Ontario'
GROUP BY Region

--4. Revenue from Bottom 10 Customers
select top 10 [Customer Name], SUM(Sales) AS Sales 
	from KMS
GROUP BY [Customer Name]
ORDER BY Sales asc

--5. Maximum Shipping cost using Shipping method
select [Ship Mode], SUM([Shipping Cost]) as [Total Shipping Cost]
from KMS
group by [Ship Mode]
order by [Total Shipping Cost] desc

--6. Revenue from Top 10 Customers to determine Most valuable customers and Product category they typically purchase
select top 10 [Customer Name], SUM(Sales) AS Sales, [Product Category] 
	from KMS
GROUP BY [Customer Name], [Product Category]
ORDER BY Sales DESC

--7. Small business Customer with the Highest sales
select [Customer Name], [Customer Segment], SUM(Sales) AS Sales 
	from KMS
where [Customer Segment] = 'Small Business'
GROUP BY [Customer Segment], [Customer Name]
ORDER BY Sales DESC

--8. Corporate Customers with the Highest number of Orders
select [Customer Name], [Customer Segment], Count([Order Quantity]) AS Orders
	from KMS
where [Customer Segment] = 'Corporate'
GROUP BY [Customer Segment], [Customer Name]
ORDER BY Orders DESC

--9. Most profitable Consumer Customer 
select [Customer Name], [Customer Segment], SUM(Profit) AS Profits
	from KMS
where [Customer Segment] = 'Consumer'
GROUP BY [Customer Segment], [Customer Name]
ORDER BY Profits DESC

--10. Comparing Sales made from Delivery Truck and Express Air 
select [Ship Mode], SUM([Shipping Cost]) AS [Shipping Cost], SUM(Sales) AS Sales, SUM([Shipping Cost])*100/SUM(Sales) AS [Percentage Shipping Cost] 
	from KMS
where [Ship Mode] IN ('Delivery Truck', 'Express Air')
GROUP BY [Ship Mode]
```
### Project Material
![Download Data here][KMS Sql Case Study.xlsx](https://github.com/user-attachments/files/21230916/KMS.Sql.Case.Study.xlsx)


