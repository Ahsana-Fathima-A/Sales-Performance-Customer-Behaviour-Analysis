# Calculated Columns & Tables Documentation

## Project: Sales Performance & Customer Behaviour Analysis

This document contains the calculated columns and calculated table created using DAX in Power BI.

---

## 1. Dim_Date Calculated Columns

### 1.1 Month Name

```dax
Month Name =
FORMAT(Dim_Date[Date], "MMMM")
```

**Purpose:** Extracts the full month name from the date column.

### 1.2 Month Number

```dax
Month Number =
MONTH(Dim_Date[Date])
```

**Purpose:** Extracts the numerical month value (1–12), supporting chronological month sorting.

### 1.3 Month Start

```dax
Month Start =
DATE(
    YEAR(Dim_Date[Date]),
    MONTH(Dim_Date[Date]),
    1
)
```

**Purpose:** Creates the first date of each month to support monthly grouping and relationships.

### 1.4 Quarter

```dax
Quarter =
"Q" & QUARTER(Dim_Date[Date])
```

**Purpose:** Identifies the quarter of each date (Q1, Q2, Q3, Q4).

### 1.5 Year

```dax
Year =
YEAR(Dim_Date[Date])
```

**Purpose:** Extracts the year from the date column for yearly analysis.

### 1.6 Year Month

```dax
Year Month =
FORMAT(Dim_Date[Date], "YYYY-MMMM")
```

**Purpose:** Combines the year and full month name for monthly reporting.

---

## 2. Dim_Month Calculated Table

### 2.1 Dim_Month

```dax
Dim_Month =
SUMMARIZE(
    Dim_Date,
    Dim_Date[Month Start],
    Dim_Date[Year],
    Dim_Date[Month Number],
    Dim_Date[Month Name],
    Dim_Date[Quarter],
    Dim_Date[Year Month]
)
```

**Purpose:** Creates a monthly dimension table from Dim_Date, containing distinct combinations of month-related attributes.

This table supports monthly sales analysis and sales target comparisons.

---

## 3. Summary

The calculated columns provide additional date attributes for time-based analysis, while the Dim_Month calculated table provides a monthly reference for connecting sales transactions with sales target information.