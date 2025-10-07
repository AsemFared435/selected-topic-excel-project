# 📊 Sales Analysis Dashboard Project

## 📋 Overview

This project involves analyzing a sales dataset for a retail or distribution business operating across the United States. The data spans from 2020 to 2021 and includes detailed information on sales orders, customer behavior, profits, and regional performance. 

### Key Entities

- **Sales Orders**: Over 7,991 orders with details like order number, sales channel (In-Store, Online, Distributor, Wholesale), dates (procured, ordered, shipped, delivered), currency (USD), quantities, discounts, unit prices, costs, and links to sales teams, customers, stores, and products.
- **Store Locations**: 367 stores with geographic details such as city, county, state, latitude/longitude, population, income metrics, and time zones.
- **Sales Teams**: 28 team members assigned to regions (Northeast, South, West, Midwest).
- **Regions**: Mapping of US states to four major regions (Northeast, South, West, Midwest).
- **Customers**: 50 customers, primarily companies (e.g., Avon Corp, Medline).
- **Products**: 47 product categories (e.g., Cookware, Photo Frames, Computers).

The dataset provides a comprehensive view of sales performance, allowing for insights into revenue trends, customer segmentation, profitability, and operational efficiency.

---

## 💡 Project Idea

The goal of this project is to transform raw sales data into actionable insights using **Microsoft Excel's Power Tools** (Power Query, Power Pivot, and PivotTables/Charts). By cleaning, modeling, and visualizing the data, we create interactive dashboards to highlight key business metrics such as revenue distribution, customer contributions, and profit margins. 

This enables stakeholders to:
- Identify growth opportunities
- Optimize sales channels
- Address underperforming areas

The project demonstrates end-to-end data analysis: from data ingestion and preparation to advanced modeling and visualization, ultimately presenting findings in three focused dashboards: **Revenue Analysis**, **Customer Analysis**, and **Profit Analysis**.

---

## 🔧 Project Steps

### 1. Data Ingestion with Power Query
- Imported raw data from the provided sources (e.g., CSV or Excel sheets) into a new Excel workbook.
- Used Power Query to connect to sheets like "Sales Orders Sheet," "Dim_StoreLocations," "Sales Teams," "Regions," "Customers," and "Products."
- Performed data cleaning: Removed duplicates, handled missing values, formatted dates and numbers, and split/merged columns as needed (e.g., ensuring consistent date formats and numeric types for prices/costs).

### 2. Data Transformation in Power Query
- Applied transformations: Filtered irrelevant rows, added calculated columns (e.g., total revenue per order as `Order Quantity × Unit Price × (1 - Discount Applied)`), and aggregated preliminary summaries.
- Merged tables using common keys (e.g., joined Sales Orders with Stores on `_StoreID`, with Regions on `StateCode`, with Sales Teams on `_SalesTeamID`, etc.) to create a unified dataset.
- Loaded the transformed queries into the Excel Data Model for further analysis.

### 3. Data Modeling in Power Pivot
- Built relationships between tables in the Data Model (e.g., one-to-many from Customers to Sales Orders on `_CustomerID`).
- Created DAX measures for key metrics, such as:
  - **Total Revenue**: `SUMX(SalesOrders, [Order Quantity] * [Unit Price] * (1 - [Discount Applied]))`
  - **Total Profit**: `Total Revenue - Total Cost` (where Total Cost = `SUMX(SalesOrders, [Order Quantity] * [Unit Cost])`)
  - **Gross Margin %**: `DIVIDE([Total Profit], [Total Revenue])`
  - **Average Order Value (AOV)**: `DIVIDE([Total Revenue], DISTINCTCOUNT(SalesOrders[OrderNumber]))`
  - **Average Orders per Customer**: `DIVIDE([Number of Orders], DISTINCTCOUNT(SalesOrders[_CustomerID]))`
  - Other measures like Total Quantity, Number of Orders, Cost %, etc.
- Validated the model by testing measures in PivotTables.

### 4. Analysis and Visualization
- Created PivotTables to slice data by dimensions (e.g., by month, region, channel, customer).
- Built charts (line, bar, pie) and slicers (e.g., for Year, Region, Sales Channel) to make dashboards interactive.
- Extracted insights by analyzing trends, top performers, and breakdowns.
- Assembled three dashboard pages in Excel: Revenue Analysis, Customer Analysis, and Profit Analysis.

### 5. Final Output
- Dashboards with key KPIs, charts, and slicers for dynamic exploration.
- Derived insights to guide business decisions, such as targeting high-profit channels or top customers.

---

## 📈 Insights from Dashboards

### 📊 Revenue Analysis Insights

#### 💰 Overall KPIs
- **Total Revenue**: $82.69M
- **Total Profit**: $30.87M
- **Total Cost**: $51.81M
- **Total Quantity Sold**: 36,162 units
- **Number of Orders**: 7,991

These figures indicate a strong revenue performance with a healthy profit margin (~37%) across all channels and regions.

#### 📈 Revenue by Month
- Revenue gradually increases from February ($4.9M) and peaks during August–October (around $8.0M–$8.7M).
- This shows a seasonal growth pattern in the second half of the year, suggesting stronger sales activity in later months.

#### 🛒 Revenue by Channel
- **In-Store** sales dominate with $34.0M, representing the highest revenue channel.
- **Online** follows with $24.6M, showing a solid digital presence.
- **Distributor** and **Wholesale** channels lag behind with $14.8M and $9.2M, respectively.

**💡 Insight**: Most sales come from direct customer engagement (In-Store & Online) rather than intermediaries.

#### 🌍 Revenue by Region
- **West Region** leads with 35% of total revenue, followed by South (32%), Midwest (21%), and Northeast (12%).

**💡 Insight**: The business performs strongest in the Western and Southern regions, indicating key markets to maintain and expand.

#### 🏙️ Revenue by Type
- **Cities** dominate revenue generation with $66.6M, far exceeding other location types like Township ($7.3M) and Town ($3.5M).

**💡 Insight**: Urban areas are the primary revenue drivers, highlighting the importance of city-based marketing and retail strategies.

#### 🧭 Summary Insight
Overall, revenue performance is driven by In-Store urban sales in Western and Southern regions, with stronger results in the later months of the year. This indicates potential opportunities to scale online sales, and optimize regional marketing to improve revenue balance across regions.

---

### 👥 Customer Analysis Insights

#### 🧾 Overall KPIs
- **Number of Customers**: 50
- **Average Order Value (AOV)**: $10,348
- **Average Orders per Customer (AOPC)**: 160
- **Total Revenue**: $82.69M
- **Total Profit**: $30.87M

**💡 Insight**: These metrics indicate a strong customer base with high spending power and a consistent order frequency.

#### 💎 Top 10 Customers by Revenue
- The top customers, including Medline, Apotheca Ltd, Pure Group, and Ohio, generate between $1.8M–$2.3M each.
- The top 10 customers together account for a significant share of total revenue, highlighting high revenue concentration among a small group.

**💡 Insight**: Building loyalty programs for top customers can help maintain long-term profitability.

#### 🌍 AOPC by Region
- **South Region** leads with 51 average orders per customer, followed by West (56) and Midwest (33).
- **Northeast** shows the lowest AOPC (19), suggesting lower engagement in that area.

**💡 Insight**: The South and West regions have more active and loyal customers, while the Northeast region may need engagement strategies.

#### 🛒 AOPC by Channel
- **In-Store Channel** dominates with 66 AOPC, followed by Online (49) and Distributor (28).
- **Wholesale** customers are the least active with only 18 average orders.

**💡 Insight**: In-store customers remain the most consistent buyers, showing the strength of physical retail interactions.

#### 📈 Total Revenue & AOV by Month
- Both Total Revenue and Average Order Value follow a similar pattern — increasing during May to October, peaking around August ($8.1M).
- The consistency of both metrics suggests stable purchasing behavior rather than sporadic large orders.

**💡 Insight**: The mid-to-late months represent peak customer activity, ideal for campaigns and promotions.

#### 🧭 Summary Insight
The customer base is highly valuable but concentrated, with a few top clients generating most of the revenue. In-store and Southern region customers drive the strongest engagement, while Northeast and Wholesale segments show growth potential. There's a clear seasonal rise in both revenue and order value, emphasizing the need for strategic marketing during mid-year periods.

---

### 💰 Profit Analysis Insights

#### 🧾 Overall KPIs
- **Total Profit**: $30.87M
- **Gross Margin**: 37.34%
- **Total Cost**: $51.82M
- **Cost Percentage**: 62.66%
- **Total Revenue**: $82.69M

**💡 Insight**: The company maintains a strong profitability ratio, with costs well-managed relative to revenue.

#### 📈 Profit by Month
- Profit shows steady growth after February, rising from $1.9M to over $3.2M by October–November.
- The second half of the year records the highest profitability, aligning with the revenue seasonality pattern.

**💡 Insight**: Profitability is strongly linked to sales growth periods, highlighting effective cost control during high-demand months.

#### 🛒 Profit by Channel
- **In-Store** channel leads with $12.7M profit, followed by Online ($9.1M), Distributor ($5.5M), and Wholesale ($3.5M).

**💡 Insight**: Direct selling channels (In-Store & Online) are the most profitable, while indirect channels yield smaller margins.

#### 🌍 Profit by Region
- **West Region** dominates with 35% of total profit, followed by South (32%), Midwest (21%), and Northeast (12%).

**💡 Insight**: Profit distribution closely mirrors the revenue breakdown, confirming consistent cost efficiency across high-performing regions.

#### 📦 Profit & Cost% by Product
- The **Accessories** category achieves the highest profit ($908.8K), while other strong performers include Bathroom Furniture, Collectibles, and Platters.
- Some products show higher cost percentages, suggesting potential to improve margins by optimizing pricing or sourcing strategies.

**💡 Insight**: Product-level analysis highlights where to focus for better profitability — high-cost, moderate-profit products can be improved through cost reduction.

#### 🧭 Summary Insight
Overall, profit performance is strong and well-balanced across key channels and regions. The In-Store channel and Western region are the main drivers of profit, while cost management remains consistent across the board. Future optimization could focus on reducing product-specific costs to boost total margins even further.

---

## 🚀 Technologies Used

- Microsoft Excel
- Power Query
- Power Pivot
- DAX (Data Analysis Expressions)
- PivotTables & PivotCharts

👥 Team Members
<div align="center">
<table>
<tr>
<td align="center">
<a href="https://github.com/hamedgebril">
<img src="https://github.com/hamedgebril.png" width="150px;" alt="Hamed Gebril"/>
</a>
<br />
<sub><b>Hamed Gebril</b></sub>
<br />
📊 Data Science Student
<br />
<a href="https://github.com/hamedgebril">
<img src="https://img.shields.io/badge/GitHub-Profile-blue?style=flat-square&logo=github" alt="GitHub Profile"/>
</a>
</td>
<td align="center">
<a href="https://github.com/AsemFared435">
<img src="https://github.com/AsemFared435.png" width="150px;" alt="Asem Fared"/>
</a>
<br />
<sub><b>Asem Fared</b></sub>
<br />
📊 Data Science Student
<br />
<a href="https://github.com/AsemFared435">
<img src="https://img.shields.io/badge/GitHub-Profile-blue?style=flat-square&logo=github" alt="GitHub Profile"/>
</a>
</td>
</tr>
</table>
</div>

---
