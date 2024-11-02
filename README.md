# Capstone-Project-Sales-Data

### Project Outline :

-(Project Title)




### Project Title : Sales Performance Analysis for a Retail Store

### 📊 Project Overview

This project analyzes the sales performance of a retail store and seeks to uncover key insights such as top selling products, regional performance and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings. By analyzing the various parameters in the data received,we seek to gatherinsights enough to make reasonable decisions which then enables us tell compelling stories around our data.

### 📂 Dataset

The dataset used in this project contains sales transactions in 2023 and 2024. It includes the following fields:
- #### Order ID
- #### Customer ID
- #### Product
- #### Region
- #### Order date
- #### Quantity
- #### Unit Price

------------

### 🧰 Tools Used

- Microsoft Excel: For initial data exploration and pivot table analysis

- Structured Query Language (SQL): For Data Querying and Analysis
  
- Power BI: For building interactive dashboards and visualizations

---------
### 🔍 Analysis Steps

#### 1. Data Cleaning

- Ensured there were no duplicate records and missing values

- Ensured that product names and customer regions were standardized.

#### 2. Exploratory Data Analysis (EDA)

- Analyzed sales trends over time (monthly,quarterly)

- Investigated geographical trends to identify high performing regions

- Identified top-selling products

#### *Pivot Table Visualzations:*

![SD pivot table 1](https://github.com/user-attachments/assets/67172c9c-fc93-46d2-aeb8-56edcd1d7da2)
![SD pivot table 2](https://github.com/user-attachments/assets/83d5dbc4-2879-4c94-a38b-f0943084c03b)
![SD pivot table 7](https://github.com/user-attachments/assets/c77b2c75-c045-4f53-b26f-f10e0f27947b)
![SD pivot table 6](https://github.com/user-attachments/assets/b07bcc9f-ee3d-4bab-a75d-e29b2a46701e)


![SD pivot table 3](https://github.com/user-attachments/assets/68075bfa-1e01-4cb9-8a0e-10452cd43eba)
![SD pivot table 4](https://github.com/user-attachments/assets/e2ac6da8-faed-4ed0-9378-eefebfa0d2a8)



#### 3. Data Analysis

Here, I used Basic Excel functions to calculate the Average sales per product and total revenue by region using the AverageIF and SUMIF functions.
Below is a sample of the arguments used.

```Excel
=AVERAGEIF($C$2:$C$50001,P5,$F$2:$F$50001)
```

```Excel
=SUMIF($D$2:$D$50001,P15,$H$2:$H$50001)
```

I was also able to perform some calculations such as the percentage of total sales contributed by each region, monthly sales totals for the current year and total revenue per product using SQL. Using SQL, I was able to gain more insight into the sales by finding the top 5 customers by total purchase amount,products with no sales in the last quarter and the highest-selling product by total sales value. Below are some of the queries used;

**To find the total sales for each product category**:

```SQL
Select sum([Quantity]) as TotalSales,[Product]from [dbo].[LITA Capstone sales data]
Group by [Product]
Order by 1 desc
```

**To find the number of sales transactions in each region**:

```SQL
Select COUNT([Product]) as salestransactions, [Region] from [dbo].[LITA Capstone sales data]
Group by [Region]
```

**To find the top 5 customers by total purchase amount**:

```SQL
select top(5) sum([Quantity]) as Top5customers, [Customer_Id] from [dbo].[LITA Capstone sales data]
Group by [Customer_Id]
order by 1 desc
```
**To find products with no sales in the last quarter**:

```SQL
select sum([Quantity]) as monthlysales, [Month], [Product]from [dbo].[LITA Capstone sales data]
where [Years]=2024 and [Month] >9
group by [Month], [Product]
```
**To find the highest-selling product by total sales value**:

```SQL
Select sum([Quantity]) as TotalSales,[Product]from [dbo].[LITA Capstone sales data]
Group by [Product]
Order by 1 desc
```

**To find the total revenue per product**:

```SQL
Alter table [dbo].[LITA Capstone sales data]
Add Revenue int
update [dbo].[LITA Capstone sales data]
set [Revenue] =[Quantity]*[UnitPrice]
Select sum([Revenue]) as TotalRevenue,[Product]from [dbo].[LITA Capstone sales data]
Group by [Product]
```

**To calculate monthly sales totals for the current year**:

```SQL
alter table [dbo].[LITA Capstone sales data]
add Years int
update [dbo].[LITA Capstone sales data]
set Years= YEAR([OrderDate])
alter table [dbo].[LITA Capstone sales data]
add Month int
update [dbo].[LITA Capstone sales data]
set[Month] = month([OrderDate])
select * from [dbo].[LITA Capstone sales data]
select sum([Quantity]) as monthlysales,[Month] from [dbo].[LITA Capstone sales data]
where [Years]=2024
group by [Month]
```

**To calculate the percentage of total sales contributed by each region**:

```SQL
select * from [dbo].[LITA Capstone sales data]
select sum ([Quantity]) as totalsale from [dbo].[LITA Capstone sales data]
alter table [dbo].[LITA Capstone sales data]
add Percentagesales decimal (10,5)
update [dbo].[LITA Capstone sales data]
set[Percentagesales] =(cast([Quantity] as decimal)/3450.000000)
Select sum([Percentagesales]) as percentageSales, [Region] from [dbo].[LITA Capstone sales data]
Group by [Region]
```

#### 4. Visualization

- Created interactive dashboards to visualize:

  - Quarterl/Yearly sales trends
 
  - Top-performing products
 
  - Sales distribution across regions

The visualization dashboard is shown below;

![sd dashboard](https://github.com/user-attachments/assets/e723d181-a416-4ef6-a386-1c06b4b737bb)


------------------------
### 💡 Key Findings

- #### Top-performing Products:
The top 3 performing products were Hats, Shirts and Shoes with Hats being the highest selling product in the year 2023 (35,000 sales) and 2024(45,000 sales) having a total of 80000 sales. having the most sale (45000) in the Eastern region in the month of March.  A consistency is seen in the sale of Hats in the East in the month of March in the previous years. Hence the need to consider stocking up on Hats in the said month in the Eastern to ensure sales.



- #### Regional Sales Performance:
The South had the highest sales in 2023 and 2024. However, there was a decline in sales in 2024 in all the regions. It is important that the possible causes of the this is looked into avoid reoccurence in the subsequent years.

- #### Under-performing Products:
Socks and Jacket are the two most under-performing products. It is also noticeable that the sale of these items in April in the West and May in the North respectively were consistently low in the both years. 

- #### Yearly/Quarterly Sales Performance:
There was an overall decrease in sales of the products from 195,000 in 2023 to 150,000 in 2024. There was a significant increase in sales in Qtr1 (72,500) and Qtr2(47,500) in 2024 from what it was in 2023, 55,000 and 32,500 respectively. Also, there was a decrease in sales in Qtr3 from 57,500 in 2023 to 30,000 in 2024 with no sale at all in Qtr4 of 2024.
Overall, there Qtr1 had the most sales(127,500), followed by Qtr3(87,500), then Qtr2(80,000) and then Qtr4(50,000).

Analysis also shows that February and June were on the average the most performing months whereas, May and December were on the average, the two most under-perfoming months.

![sd visuals3](https://github.com/user-attachments/assets/1b0ad229-f209-45d9-a64d-b9f54f30f1a0)
![sd visuals4](https://github.com/user-attachments/assets/474b5feb-7f63-4edb-b845-e896a440e449)
![sd visuals4](https://github.com/user-attachments/assets/b376b3ec-56e8-4167-a937-7c79dd97594b)

