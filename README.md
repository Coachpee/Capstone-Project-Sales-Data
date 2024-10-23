# Capstone-Project-Sales-Data

### Project Title : Sales Performance Analysis for a Retail Store

### 📊 Project Overview

This project analyzes the sales performance of a retail store and seeks to uncover key insights such as top selling products, regional performance and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings. By analyzing the various parameters in the data received,we seek to gatherinsights enough to make reasonable decisions which then enables us tell compelling stories around our data.

### 📂 Dataset

The dataset used in this project contains sales transactions in 2023 and 2024. It includes the following fields:
- #### Order ID
- #### Customer ID
- #### Product
- #### Region
- #### Order Date
- #### Quantity
- #### Unit Price

You can find the dataset [here] (

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

- Identified high-selling products

![EDA for sales data](https://github.com/user-attachments/assets/ea08d837-a66d-45b5-a1c1-a57c929eca49)

![EDA for sales data2](https://github.com/user-attachments/assets/64df48e9-d05a-467d-a6fa-ddbc4879fa4a)

#### 3. Data Analysis

Here, I used Basic Excel functions to run some analysis such as average sales per product and total revenue by region using the AverageIF anf SUMIF formulas. Below is a sample of the formulas used.

```Excel
=AVERAGEIF($C$2:$C$50001,P5,$F$2:$F$50001)
```

```Excel
=SUMIF(D3:D50002,P16,H3:H50002)
```


#### 3. Visualization

- Created interactive dashboards to visualize:

  - Monthly sales trends
 
  - Top-performing products and customers
 
  - Sales distribution across regions

Visualizations can be found [here]

------------------------
### 💡 Key Findings

- #### Top-performing Products:
The top 3 performing products were Hats, Shirts and Shoes with Hats being the highest selling product in the year 2023 and 2024 with a total of 80000 sales, having the most sale (45000) in the Eastern region in the month of March.  A consistency is seen in the sale of Hats in the East in the month of March in the previous years. Hence the need to consider stocking up on Hats in the said month in the Eastern to ensure sales.

- #### Regional Sales Performance:
The South had the highest sales in 2023 and 2024. However, there was a decline in sales in 2024 in all the regions. It is important that the possible causes of the this is looked into avoid reoccurence in the subsequent years.

- #### Under-performing Products:
Socks and Jacket are the two most under-performing products. It is also noticeable that the sale of these items in April in the West and May in the North respectively were consistently low in the both years. 

- #### Monthly/Quarterly Sales Performance:
There was a significant increase in sales in Qtr1 and Qtr2 in 2024 from what it was in 2023. Also, there was a decrease in sales in Qtr3 of 2024 with no sale in Qtr4 of 2024.
Analysis also shows that April and May  were the two most under-perfoming months in the both years.
