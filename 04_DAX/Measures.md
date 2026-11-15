# DAX Measures Documentation

## Project: Sales Performance & Customer Behaviour Analysis

This document contains the DAX measures developed for the Power BI dashboard, organised according to their analytical purpose.

---

## 1. Core Sales Measures

### 1.1 Total Sales

```dax
Total Sales =
SUM(Fact_Sales[Sales])
```

**Purpose:** Calculates the total sales revenue.

### 1.2 Total Profit

```dax
Total Profit =
SUM(Fact_Sales[Profit])
```

**Purpose:** Calculates the total profit generated from sales transactions.

### 1.3 Total Quantity

```dax
Total Quantity =
SUM(Fact_Sales[Quantity])
```

**Purpose:** Calculates the total quantity of products sold.

---

## 2. Profitability Measures

### 2.1 Average Sales per Order

```dax
Average Sales per Order =
DIVIDE(
    [Total Sales],
    DISTINCTCOUNT(Fact_Sales[Order ID]),
    0
)
```

**Purpose:** Calculates the average sales revenue generated per order.

### 2.2 Profit Margin

```dax
Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
```

**Purpose:** Measures the percentage of sales revenue retained as profit.

---

## 3. Target Performance Measures

### 3.1 Sales Target

```dax
Sales Target =
SUM(Sales_Target[Target Sales])
```

**Purpose:** Calculates the total sales target based on the selected filter context.

### 3.2 Sales Variance

```dax
Sales Variance =
IF(
    ISBLANK([Sales Target]),
    BLANK(),
    [Total Sales] - [Sales Target]
)
```

**Purpose:** Calculates the difference between actual sales and the sales target.

### 3.3 Target Achievement %

```dax
Target Achievement % =
DIVIDE(
    [Total Sales],
    [Sales Target]
)
```

**Purpose:** Calculates the percentage of the sales target achieved.

### 3.4 Sales Target (Overall)

```dax
Sales Target (Overall) =
CALCULATE(
    [Sales Target],
    REMOVEFILTERS(Fact_Sales[Region])
)
```

**Purpose:** Calculates the overall sales target while removing the Region filter from Fact_Sales.

### 3.5 Target Achievement % (Overall)

```dax
Target Achievement % (Overall) =
DIVIDE(
    [Total Sales],
    [Sales Target (Overall)]
)
```

**Purpose:** Calculates target achievement using the overall sales target.

---

## 4. Time Intelligence Measures

### 4.1 Previous Year Sales

```dax
Previous Year Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(Dim_Date[Date])
)
```

**Purpose:** Calculates sales for the corresponding period in the previous year.

### 4.2 Sales YoY Change

```dax
Sales YoY Change =
[Total Sales] - [Previous Year Sales]
```

**Purpose:** Calculates the absolute difference between current-year sales and previous-year sales.

### 4.3 Sales YoY Growth

```dax
Sales YoY Growth =
DIVIDE(
    [Total Sales] - [Previous Year Sales],
    [Previous Year Sales]
)
```

**Purpose:** Calculates the year-over-year percentage change in sales.

---

## 5. Customer Analysis Measures

### 5.1 Average Orders per Customer

```dax
Average Orders per Customer =
DIVIDE(
    [Total Orders],
    [Total Customers],
    0
)
```

**Purpose:** Calculates the average number of orders per customer.

### 5.2 Total Customers

```dax
Total Customers =
DISTINCTCOUNT(Fact_Sales[Customer ID])
```

**Purpose:** Counts the number of unique customers.

### 5.3 Total Orders

```dax
Total Orders =
DISTINCTCOUNT(Fact_Sales[Order ID])
```

**Purpose:** Counts the number of unique orders.

---

## 6. Product Performance Measures

### 6.1 Average Profit per Order

```dax
Average Profit per Order =
DIVIDE(
    [Total Profit],
    [Total Orders],
    0
)
```

**Purpose:** Calculates the average profit generated per order.

### 6.2 Total Product Categories

```dax
Total Product Categories =
DISTINCTCOUNT(Fact_Sales[Category])
```

**Purpose:** Counts the number of distinct product categories.

### 6.3 Total Products

```dax
Total Products =
DISTINCTCOUNT(Fact_Sales[Product ID])
```

**Purpose:** Counts the number of unique products.

---

## 7. Discount Analysis Measures

### 7.1 Average Discount

```dax
Average Discount =
AVERAGE(Fact_Sales[Discount])
```

**Purpose:** Calculates the average discount percentage across sales records.

### 7.2 Discounted Sales

```dax
Discounted Sales =
CALCULATE(
    [Total Sales],
    Fact_Sales[Discount] > 0
)
```

**Purpose:** Calculates sales revenue from transactions where a discount was applied.

### 7.3 Total Discounted Orders

```dax
Total Discounted Orders =
CALCULATE(
    DISTINCTCOUNT(Fact_Sales[Order ID]),
    Fact_Sales[Discount] > 0
)
```

**Purpose:** Counts distinct orders containing discounted sales records.

---

## 8. Summary

A total of 22 DAX measures were developed to support the dashboard's sales, profitability, target performance, time intelligence, customer, product, and discount analyses.

These measures enable dynamic calculations across dashboard visuals, KPI cards, interactive filters, and drill-through pages.

The measures are organised into display folders within the Fact_Sales table, with the two overall target measures stored under Dim_Date.