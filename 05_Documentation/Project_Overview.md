# Project Overview
## Sales Performance & Customer Behaviour Analysis

### 1. Project Introduction

The **Sales Performance & Customer Behaviour Analysis** project focuses on analyzing sales transactions to understand business performance, product profitability, customer purchasing patterns, and sales target achievement.

The project uses Power BI to transform raw sales data into an interactive dashboard that helps users explore business performance and identify meaningful trends.

### 2. Project Objectives

- Analyze overall sales, profit, and quantity performance.
- Evaluate sales performance across regions and product categories.
- Identify top-performing and low-performing products.
- Understand customer purchasing behaviour.
- Analyze sales trends over time.
- Compare actual sales against sales targets.
- Evaluate target achievement and sales variance.

### 3. Tools and Technologies

| Tool | Purpose |
|---|---|
| Power BI Desktop | Data modeling, DAX calculations, and dashboard development |
| Power Query | Data cleaning and transformation |
| DAX | Measures, calculated columns, and calculated tables |
| CSV | Source dataset format |
| GitHub | Project documentation and version control |

### 4. Dataset Overview

The project uses a Superstore sales dataset containing **9,994 records and 21 columns**.

The dataset includes information about:
- Orders and order dates
- Customers and customer segments
- Products and categories
- Sales, quantity, discount, and profit
- Regions and geographical information

A separate sales target table is also used for target performance analysis.

### 5. Data Preparation

Data preparation was performed using Power Query.

The preparation process included:
- Promoting the first row as column headers.
- Assigning appropriate data types.
- Applying Trim and Clean operations to text columns.
- Validating date, numeric, and text columns.
- Checking the transformed data for errors.

### 6. Data Model

The Power BI model consists of four tables:

1. **Fact_Sales** – Contains sales transaction data.
2. **Dim_Date** – Provides date-related information for time-based analysis.
3. **Dim_Month** – Provides month-level information for monthly analysis.
4. **Sales_Target** – Contains monthly sales target information.

The model uses active relationships to connect the fact and dimension tables.

Refer to `03_Data_Model/` for the model diagram and relationship documentation.

### 7. Dashboard Structure

The dashboard contains six pages:

| Page | Description |
|---|---|
| Sales Overview | Overall business performance and sales trends |
| Product Analysis | Product and category-level performance |
| Customer Analysis | Customer purchasing patterns and behaviour |
| Sales Target Analysis | Actual sales compared with sales targets |
| Product Performance | Drill-through analysis of individual products |
| Customer Insights | Drill-through analysis of individual customers |

### 8. Key Features

- Interactive dashboard navigation.
- Dynamic filtering using slicers.
- KPI cards for important business metrics.
- Time-based sales analysis.
- Sales target and achievement analysis.
- Product-level drill-through.
- Customer-level drill-through.
- Interactive charts and tables.

### 9. Project Outcome

The project provides an interactive view of sales performance, profitability, product performance, customer behaviour, and target achievement.

It demonstrates the use of Power BI, Power Query, data modeling, and DAX to build a multi-page business intelligence dashboard.

### 10. Project Deliverables

- Power BI dashboard file (`.pbix`)
- Dashboard screenshots
- Data model diagram and documentation
- DAX measures and calculated columns documentation
- Project documentation
- Final presentation and project report