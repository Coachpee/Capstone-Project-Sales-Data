# Capstone-Project-Sales-Data

### Project Outline :

- [Project Title](Project-Title)

- [Project Overview](Project-Overview)

- [Dataset](Dataset)

- [Tools Used](Tools-Used)

- [Analysis Steps](Analysis-Steps)

- [Key Findings](Key-Findings)

- [Recommendations](Recommendations)

- [Conclusion](Conclusion)

----------------

### Project Title : Sales Performance Analysis for a Retail Store

----------

### 📊 Project Overview

This project analyzes the sales performance of a retail store and seeks to uncover key insights such as top selling products, regional performance and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings. By analyzing the various parameters in the data received,we seek to gatherinsights enough to make reasonable decisions which then enables us tell compelling stories around our data.

---------------

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
Below is a sample of the arguments used. Using the multiplication formula, I was able to create a **Revenue column**  by multiplying the **Unit Price** with the **Quantity**. For example; =F2*G2

Below is a sample of the arguments used to run the analysis.

```Excel
=AVERAGEIF($C$2:$C$50001,P5,$F$2:$F$50001)
```

![SD excel1](https://github.com/user-attachments/assets/f16b560a-0010-44d7-8947-5b1691e60994)

```Excel
=SUMIF($D$2:$D$50001,P15,$H$2:$H$50001)
```

![SD excel2](https://github.com/user-attachments/assets/5ba8efdd-da18-4f9e-93da-80eb718c2e4c)

I was also able to perform some calculations such as the percentage of total sales contributed by each region, monthly sales totals for the current year and total revenue per product using SQL. Using SQL, I was able to gain more insight into the sales by finding the top 5 customers by total purchase amount,products with no sales in the last quarter and the highest-selling product by total sales value. Below are some of the queries used;

**To find the total sales for each product category**:

```SQL
Select sum([Quantity]) as TotalSales,[Product]from [dbo].[LITA Capstone sales data]
Group by [Product]
Order by 1 desc
```
![sdsql1](https://github.com/user-attachments/assets/dc448426-ef98-4a72-b21b-55cb9efc30ea)

**To find the number of sales transactions in each region**:

```SQL
Select COUNT([Product]) as salestransactions, [Region] from [dbo].[LITA Capstone sales data]
Group by [Region]
```
![sdsql2](https://github.com/user-attachments/assets/591be597-fb8c-4fc5-ae88-2baff74b2ea7)

**To find the top 5 customers by total purchase amount**:

```SQL
select top(5) sum([Quantity]) as Top5customers, [Customer_Id] from [dbo].[LITA Capstone sales data]
Group by [Customer_Id]
order by 1 desc
```
![sdsql6JPG](https://github.com/user-attachments/assets/88f29423-b263-44e3-9aaa-660279ac00b7)

**To find products with no sales in the last quarter**:

```SQL
select sum([Quantity]) as monthlysales, [Month], [Product]from [dbo].[LITA Capstone sales data]
where [Years]=2024 and [Month] >9
group by [Month], [Product]
```
**None of the products was sold in the last quarter.**

**To find the highest-selling product by total sales value**:

```SQL
Select sum([Quantity]) as TotalSales,[Product]from [dbo].[LITA Capstone sales data]
Group by [Product]
Order by 1 desc
```
![sdsql3](https://github.com/user-attachments/assets/57544357-3560-49c4-ad9a-23d7c2366c9d)

The highest selling product is Hats with a total sale of 80,000.

**To find the total revenue per product**:

```SQL
Alter table [dbo].[LITA Capstone sales data]
Add Revenue int
update [dbo].[LITA Capstone sales data]
set [Revenue] =[Quantity]*[UnitPrice]
Select sum([Revenue]) as TotalRevenue,[Product]from [dbo].[LITA Capstone sales data]
Group by [Product]
```

![sdsql4](https://github.com/user-attachments/assets/4206589a-168f-4a71-bc59-6c935a536b8e)

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

![sdsql5](https://github.com/user-attachments/assets/fc144926-f8bd-4db4-b0da-74c657ebeb93)

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
![sdsql7](https://github.com/user-attachments/assets/e0bd7210-2074-471a-a479-77967f2fc6b7)


#### 4. Visualization

- Created interactive dashboards to visualize:

  - Quarterly/Yearly sales trends
 
  - Top-performing products
 
  - Sales distribution across regions

The visualization dashboard is shown below;

![sd dashboard](https://github.com/user-attachments/assets/e723d181-a416-4ef6-a386-1c06b4b737bb)


------------------------
### 💡 Key Findings

- #### Top-performing Products:
  
The top 3 performing products in terms of sales were Hats(80,000) followed by Shoes(72,500) and then Shirts and Gloves with a total sale of 62,500 each.Hats were the highest selling product in the year 2023 (35,000 sales) and 2024(45,000 sales). In both 2023 and 2024, there was consistency in the sale of products in particular months of the year,with a remarkable increase in the sale of the products in those months.For instance, Gloves were sold in June, 2023(20,0000) and 2024(30,000), Hats were sold in March,2023(18,000) and 2024(28,000), Jackets were sold in May, 2023(5,000) and 2024(8,000), Shirts were sold in January,2023(13,000) and 2024(20,000),Shoes were sold in February,2023 and 2024 (25,000) and Socks in April,2023(8,000) and 2024(10,000). Shoes and Hats had the highest number of sales transactions(10,000) while Gloves,Shirt,Socks and Jackets had equal sales transactons of 8,000. The highest revenue generated was 3.09millions from the sale of Shoes. 
It is also important to notice the increase in sales for Gloves,Jackets and Socks in the colder months of the year, indicating strong seasonality.

![sd visuals7JPG](https://github.com/user-attachments/assets/c00890e8-e184-4e20-8d34-e1cf7afcad43)
![sd visuals8](https://github.com/user-attachments/assets/626da35e-1707-4fa7-9fb6-fdd318e74e67)
![sd visuals9](https://github.com/user-attachments/assets/0a033cee-fcd7-4a75-a49d-c8fd576f4540)
![sd visuals10](https://github.com/user-attachments/assets/582bc735-fff2-4de5-9b1e-e2b194b81f25)
![sd visuals11](https://github.com/user-attachments/assets/5baf8955-b244-4e78-8062-dbf80f8d2ec2)
![sd visuals12](https://github.com/user-attachments/assets/5e2cefea-1aed-474e-8fb9-87de864151a0)
![sd visuals13](https://github.com/user-attachments/assets/26e08998-f72c-4cd3-9163-788b50a7ae85)


- #### Regional Sales Performance:
  
The South had the highest sales in 2023(68,000) and 2024(55,000). In the South, there was the sales of only Gloves(50,000) and Shoes(50,000) in the months of June and February respectively, in 2024 and Socks(23,000) in October,2024, with Gloves and Shoes being the highest selling. In the North, Shirts were the highest selling products with a total of 13,000 in 2023 and 20,000 in 2024 in the month of January. Jackets had a total sale of 5,000 in 2023 and 8,000 in 2024 in the month May and Hats(18,000) in September 2023 only.The East had Hats as the highest in March with a total sales of 18,000 in 2023 and 28,000 in 2024. There was also the sales of Shoes(13,000) in July 2024, Shirts(30,000) in July 2023 and Jacket(15,000) in November 2023. The West had the sales of Socks increase from 8,0000 in 2023 to 10,000 in 2024 in the month of April. There was also the sales of Shoes(10,000) in and Hats(18,000) in August 2023 and 2024 respectively and Gloves(13,000) in December 2023.  In 2023 and 2024,in the North there was no sale of Gloves and in the South, there was no sale of Shirts. In 2024, the South had no sale of Socks, the West had no sale of Gloves, the North had no sale of Hats in 2024 and no sale of Gloves in 2023 and 2024. Toct this effect, there is need to boost marketing efforts and sales promotions in regions of low sales.

The trend in the sales of specific products at specific months of the year indicates the need for the targetted availabilty of more of those products at those times of the year and in the regions of higher sale. For instance, in the Month of June and February, the South should have so much in stock of Gloves and Shoes respectively. In the month of March, the East should have so much in stock of Hats, in the West in the month of April, Socks and the North in the month of January, Shirts and in the month of May,Jackets.

![sd visuals6](https://github.com/user-attachments/assets/419de3a4-4e4f-48ad-8bab-9441e8a1403a)
![sd visuals14](https://github.com/user-attachments/assets/25314c27-dce2-42b6-a532-2f26fc7ebade)


- #### Yearly/Quarterly Sales Performance:
  
There was an overall decrease in sales of the products from 195,000 in 2023 to 150,000 in 2024. There was a significant increase in sales in Qtr1 (72,500) and Qtr2(47,500) in 2024 from what it was in 2023, 55,000 and 32,500 respectively. Also, there was a decrease in sales in Qtr3 from 57,500 in 2023 to 30,000 in 2024 with no sale at all in Qtr4 of 2024.
Overall, there Qtr1 had the most sales(127,500), followed by Qtr3(87,500), then Qtr2(80,000) and then Qtr4(50,000).

Analysis also shows that February and June were on the average the most performing months whereas, May and December were on the average, the two most under-perfoming months.

![sd visuals3](https://github.com/user-attachments/assets/1b0ad229-f209-45d9-a64d-b9f54f30f1a0)
![sd visuals4](https://github.com/user-attachments/assets/474b5feb-7f63-4edb-b845-e896a440e449)
![sd visuals4](https://github.com/user-attachments/assets/b376b3ec-56e8-4167-a937-7c79dd97594b)


### 🔦 Recommendations:

Based on these insights, targeted strategies like **region-specific promotions**, **seasonal inventory adjustments** and **focus on high-demand products** can be developed to enhance overall sales performance and address regional demand patterns.

### 📘 Conclusion:

The sales analysis provided valuable insights into the performance of different product categories(Gloves,Shoes,Jacket.Shirts,and Socks) across the four major regions (East,West,North and South). By examining key metrics such as total revenue, total sales volume and Monyhly,Quarter and Yearly trends, we could identify the best-performing products and  and regions, we could identify the best-performing products, region as well as opportunities for improvement.
