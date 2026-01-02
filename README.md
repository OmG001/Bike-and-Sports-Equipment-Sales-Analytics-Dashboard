# 🚴🏻‍♂️ Bike & Sports Equipment Sales Analytics Dashboard

An interactive **Sales Analytics Dashboard** built using **Power BI Desktop** to analyze **sales performance, customer behavior, product performance, and returns** across multiple dimensions such as **gender, income group, region, category, and time**.
The dashboard enables business users to track KPIs, monitor trends, and perform deep drill-down analysis using **interactive visuals, custom tooltips, and detail pages**.

---

## 📌 Project Overview

This project transforms raw retail sales data into an **executive-ready Power BI dashboard** that helps organizations:

* Track overall sales and order performance
* Understand customer behavior and segmentation
* Identify top-performing and high-return products
* Compare actual vs adjusted sales
* Explore trends using time-based KPIs and tooltips

---

## 🎯 Purpose of the Project

The key objectives of this project are to:

* Monitor overall **sales performance and order trends**
* Analyze **customer behavior** by gender, income group, and parent status
* Track **returns and return percentage**
* Identify **top-selling products**
* Compare **actual sales vs adjusted sales**
* Enable deep drill-down analysis using **tooltips and detail pages**

### Suitable For

* Business intelligence portfolios
* Power BI learning projects
* Sales & retail analytics use cases

---

## 📂 Dataset Structure (Data Model)

The project uses multiple tables organized in a **star-schema–like data model**.

### Main Tables Used

* **Sales (2015, 2016, 2017)** – Transactional sales data
* **Customers** – Gender, marital status, parent status, income group, email
* **Products** – Product name, category, sub-category, price, cost
* **Product Categories & Subcategories** – Hierarchical product classification
* **Calendar** – Date table for time intelligence (Year, Quarter, Month)
* **Territories** – Country and regional information
* **Returns** – Returned orders data

### Why This Structure

* Enables clean relationships
* Improves model performance
* Makes DAX calculations scalable and efficient

---

## 🔗 Data Relationships (High Level)

* Customers → Sales (One-to-Many)
* Products → Sales (One-to-Many)
* Calendar → Sales (One-to-Many)
* Territories → Sales (One-to-Many)
* Sales → Returns (One-to-Many)

This design allows analysis from **any business angle**.

---

## 🛠 Tools & Technologies Used

### 🔹 Power BI Desktop

* Core tool for dashboard development
* Supports data modeling, DAX, and interactive visuals

### 🔹 Power Query

* Data cleaning and preparation
* Column formatting, transformations, and type corrections

### 🔹 DAX (Data Analysis Expressions)

* Used to create all KPIs and calculations
* Enables dynamic, filter-aware metrics

### 🔹 Interactive Visuals & Tooltips

* Improve user experience
* Enable deep insights without clutter

---

## 🔄 Step-by-Step Project Workflow

### 1️⃣ Data Loading

* Imported all sales, customer, product, calendar, and returns tables
* Verified correct data types

### 2️⃣ Data Cleaning (Power Query)

* Removed unnecessary columns
* Standardized column names
* Fixed date and numeric data types
* Cleaned relationship keys

### 3️⃣ Data Modelling

* Created relationships between fact and dimension tables
* Verified cardinality and filter direction
* Optimized model for reporting

### 4️⃣ DAX Measures Creation

* Created a dedicated **Measure Table**
* Implemented all KPIs as measures (Power BI best practice)

---

## 🧮 Key DAX Measures Used

### Total Sales

```DAX
TotalSales = SUM(Sales[SalesAmount])
```

### Order Count

```DAX
CountOrders = COUNT(Sales[OrderNumber])
```

### Total Return

```DAX
TotalReturn = SUM(Return[ReturnQuantity])
```

### Return Percentage

```DAX
% Return = DIVIDE([TotalReturn], [TotalQuantity])
```

### Sales Month-to-Date

```DAX
SalesMTD = TOTALMTD([TotalSales], Calendar[Date])
```

### Previous Month Sales

```DAX
PreviousMonthSales =
CALCULATE(
    [TotalSales],
    PREVIOUSMONTH(Calendar[Date])
)
```

### Yearly Total Sales

```DAX
YearlyTotalSales =
CALCULATE(
    [TotalSales],
    ALLEXCEPT(Calendar, Calendar[Year])
)
```

### Growth Percentage

```DAX
%GrowthSales =
DIVIDE(
    [TotalSales] - [PreviousMonthSales],
    [PreviousMonthSales]
)
```

### Rolling 3-Month Average

```DAX
3MonthRollingAverage =
AVERAGEX(
    DATESINPERIOD(
        Calendar[Date],
        MAX(Calendar[Date]),
        -3,
        MONTH
    ),
    [TotalSales]
)
```

---

## 📊 Dashboard Pages Explained

### 📄 Page 1: Sales Overview

**Purpose:** High-level monitoring of sales performance.

**Key Elements**

* KPI Cards:

  * Total Sales
  * Order Count
  * Total Return
  * % Return
* Sales by Sub-Category & Income Group
* Sales by Country (Map)
* Top Products by Order Count
* Sales vs Adjusted Sales Trend
* Monthly Sales & Order Goals

**Slicers**

* Gender
* Year / Quarter
* Category
* Region

---

### 📄 Page 2: Product Sales Details

**Purpose:** Deep product-level and customer-level analysis.

**Key Elements**

* Selected Product Price & Cost
* Customer-level sales table
* Sales by Marital Status
* Sales by Parent Status
* Sales trends by Year and Country

---

## 🧩 Custom Tooltip (Advanced Feature)

This project includes **custom Power BI tooltips** to show detailed insights on hover without cluttering the dashboard.

### 🎯 Purpose of Custom Tooltips

* Provide additional context without adding extra visuals
* Enable quick drill-down analysis
* Improve usability and interactivity

### 🔧 How the Tooltip Was Built

* Created a dedicated tooltip page
* Enabled **Tooltip = On** and **Page Size = Tooltip**
* Added KPI cards, tables, and compact charts
* Reused existing DAX measures for accuracy
* Linked tooltip page to main visuals

Power BI automatically passes context (product, customer, date, category) to the tooltip.

### Where Tooltips Are Used

* Product name visuals
* Sales by category charts
* Order count visuals
* Customer-level tables

---

## 📌 Key Business Insights

* Sales are almost evenly split across genders
* High-income customers contribute significantly to total revenue
* Certain products dominate order volume
* Returns are measurable and trackable
* Sales show clear seasonal and monthly trends
* Adjusted sales help simulate pricing scenarios

---

## 💼 Business Value

* Helps sales managers track performance
* Enables customer segmentation analysis
* Supports product and pricing decisions
* Provides quick executive-level insights

---

## ▶️ How to Use the Dashboard

1. Open the report in **Power BI Desktop**
2. Use slicers to filter by:

   * Gender
   * Category
   * Region
   * Time
3. Hover over visuals to view tooltips
4. Drill into product-level details
5. Compare KPIs against goals

---

## 📝 Project Summary

> Built an interactive Power BI sales dashboard using a star-schema data model and advanced DAX measures to analyze sales, returns, customer behavior, and product performance, including custom tooltips and time-based KPIs.

---
