# Data Model Documentation

## 1. Overview

The Sales Performance & Customer Behaviour Analysis project uses a relational data model developed in Microsoft Power BI.

The model connects sales transactions, date information, and monthly sales targets to support interactive analysis and reporting.

## 2. Tables Used

### Fact_Sales
The central fact table containing transactional sales information.

Key columns include:
- Order ID
- Order Date
- Customer ID
- Customer Name
- Product ID
- Product Name
- Category
- Sub-Category
- Sales
- Profit
- Quantity
- Discount
- Month Start

### Dim_Date
A date dimension table used for date-based analysis.

It supports:
- Daily analysis
- Monthly analysis
- Quarterly analysis
- Yearly analysis

### Dim_Month
A monthly dimension table used for monthly sales and target analysis.

It contains:
- Month Name
- Month Number
- Month Start
- Quarter
- Year

### Sales_Target
Contains monthly sales target information.

Key columns include:
- Month Name
- Month Start
- Target Sales
- Year

## 3. Relationships

Three active relationships were established in the Power BI data model.

| From Table | Column | To Table | Column | Cardinality |
|---|---|---|---|---|
| Dim_Date | Date | Fact_Sales | Order Date | One-to-Many |
| Dim_Month | Month Start | Fact_Sales | Month Start | One-to-Many |
| Dim_Month | Month Start | Sales_Target | Month Start | One-to-Many |

All three relationships use single-direction filtering from the dimension/month table side to the related fact table side.

## 4. Data Modelling Approach

The model uses a central sales fact table connected to supporting date and monthly tables.

This structure supports:

- Organised transactional and reference data.
- Daily, monthly, quarterly and yearly analysis.
- Monthly sales and target comparisons.
- Interactive filtering across dashboard pages.
- Product and customer drill-through analysis.

## 5. Role of the Data Model

The data model supports the six dashboard pages:

1. Sales Overview
2. Product Analysis
3. Customer Analysis
4. Sales Target Analysis
5. Product Performance
6. Customer Insights

## 6. Conclusion

The data model provides the foundation for the Power BI report by connecting sales transactions, date information, and monthly target data.

The relationships enable consistent filtering and support the analysis of sales performance, profitability, product performance, customer behaviour, and target achievement.