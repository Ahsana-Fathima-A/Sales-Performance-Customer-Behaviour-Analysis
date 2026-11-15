# Data Dictionary
## Sales Performance & Customer Behaviour Analysis

This document describes the main tables and fields used in the Power BI project.

## 1. Fact_Sales

**Purpose:** Stores individual sales transaction records and related business information.

| Column | Description |
|---|---|
| Row ID | Unique identifier for a transaction row |
| Order ID | Unique order identifier |
| Order Date | Date when the order was placed |
| Ship Date | Date when the order was shipped |
| Ship Mode | Shipping method used |
| Customer ID | Unique customer identifier |
| Customer Name | Customer's name |
| Segment | Customer segment |
| Country | Country associated with the order |
| City | City associated with the order |
| State | State associated with the order |
| Postal Code | Postal code associated with the order |
| Region | Sales region |
| Product ID | Unique product identifier |
| Category | Product category |
| Sub-Category | Product sub-category |
| Product Name | Product name |
| Sales | Sales amount |
| Quantity | Quantity sold |
| Discount | Discount applied |
| Profit | Profit generated |

**Additional field:**

| Column | Description |
|---|---|
| Month Start | Month-level date field used for monthly analysis and relationships |

## 2. Dim_Date

**Purpose:** Provides date-related attributes for time-based analysis.

| Column | Description |
|---|---|
| Date | Calendar date |
| Year | Year extracted from the date |
| Quarter | Quarter derived from the date |
| Month Name | Full month name |
| Month Number | Numeric month value |
| Month Start | First day of the corresponding month |
| Year Month | Year and month formatted together |

## 3. Dim_Month

**Purpose:** Provides month-level information for monthly sales and target analysis.

| Column | Description |
|---|---|
| Month Start | First day of the month |
| Year | Calendar year |
| Month Number | Numeric month value |
| Month Name | Full month name |
| Quarter | Quarter associated with the month |
| Year Month | Year and month formatted together |

## 4. Sales_Target

**Purpose:** Stores monthly sales target information used to evaluate actual sales performance.

| Column | Description |
|---|---|
| Month Start | Month associated with the sales target |
| Target Sales | Sales target amount |

## 5. Table Relationships

The Power BI model contains the following active relationships:

| One-side table and column | Many-side table and column |
|---|---|
| Dim_Date[Date] | Fact_Sales[Order Date] |
| Dim_Month[Month Start] | Fact_Sales[Month Start] |
| Dim_Month[Month Start] | Sales_Target[Month Start] |

All three relationships use active, single-direction filtering from the one-side table to the many-side table.

## 6. Notes

- Fact_Sales is the main transaction table.
- Dim_Date supports date-based analysis.
- Dim_Month supports monthly sales and target analysis.
- Sales_Target is used for comparing actual sales with monthly targets.
- The Month Start field connects transaction and target data at the monthly level.