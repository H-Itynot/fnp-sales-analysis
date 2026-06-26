# Methodology

This document outlines the process used to clean, model, and analyze the FNP sales dataset in Excel.

## 1. Data Source

The dataset is a publicly available, simulated dataset designed to model FNP (Ferns & Petals) style gifting and floral sales. It is split across three CSV files:

- **customers.csv** — 100 rows: Customer_ID, Name, City, Contact_Number, Email, Gender, Address
- **orders.csv** — 1,000 rows: Order_ID, Customer_ID, Product_ID, Quantity, Order_Date, Order_Time, Delivery_Date, Delivery_Time, Location, Occasion
- **products.csv** — 70 rows: Product_ID, Product_Name, Category, Price (INR), Occasion

## 2. Data Cleaning (Power Query)

The raw data was loaded into Power Query for cleaning and shaping prior to building the data model. Real data quality issues identified and addressed in this dataset included:

- **Inconsistent date formats within the same column.** `Order_Date` and `Delivery_Date` mix multiple formats in the same field (e.g. `24-02-2023`, `7/11/2023`, `5/3/2023`), which required standardizing to a single date type before any date based calculations or relationships would work correctly.
- **Multi-line address fields.** The `Address` column in customers.csv contains embedded line breaks within a single cell (e.g. a building/street number on one line and the city/postal code on the next), which needed to be handled carefully during import so the address stayed intact as one field rather than splitting across columns.
- **Mixed contact number formats.** Some `Contact_Number` values appear in scientific notation (e.g. `9.17194E+11`) due to Excel auto-formatting long numeric strings, requiring conversion back to text/proper number format to preserve the full phone number.
- Removing duplicate rows and blank records
- Standardizing text casing and trimming whitespace in category, product, and city fields
- Validating numeric fields (Price, Quantity) for correct data types before loading to the model

## 3. Data Modeling (Power Pivot)

Cleaned tables were loaded into the Excel Data Model via Power Pivot. Relationships were established between:

- Orders and Customers (by Customer ID)
- Orders and Products (by Product ID)
- Orders and Date table (by Order Date and Delivery Date, using a dedicated calendar table for time intelligence)

> Note: Confirm the exact table names and relationship keys used in your model so this matches your actual schema.

## 4. DAX Measures

Key measures were written to power the dashboard KPIs and visuals, including:

- **Total Revenue** — sum of order level revenue across the fact table
- **Total Orders** — distinct count of order IDs
- **Total Customers** — distinct count of customer IDs
- **Average Order to Delivery Time** — average of the difference between Delivery Date and Order Date, in days
- **Average Customer Spending** — Total Revenue divided by Total Customers

> Note: Replace these descriptions with your actual DAX formulas, for example:
> ```
> Total Revenue = SUM(Orders[Revenue])
> Avg Order Delivery Time = AVERAGEX(Orders, Orders[Delivery Date] - Orders[Order Date])
> Avg Customer Spending = DIVIDE([Total Revenue], [Total Customers])
> ```
> Swap in the exact formulas you used so the methodology accurately reflects the workbook.

## 5. Dashboard Build

PivotTables and PivotCharts were connected to the Power Pivot data model to build each visual:

- Bar charts for Revenue by Occasion, Revenue by Category, Top 5 Products by Revenue, and Top 10 Cities by Orders
- Line charts for Revenue by Hour and Revenue by Month
- KPI cards built from single-value PivotTables tied to the DAX measures above
- Slicers for Order Date, Delivery Date, and Occasion connected across all PivotCharts for synchronized filtering

## 6. Validation

Before finalizing the dashboard, totals were spot checked against raw data subtotals (e.g. SUM and COUNTIFS on the source table) to confirm the Power Pivot measures matched expected values.

> Note: If you did any specific validation steps (e.g. cross-checking totals against a pivot built directly on raw data), add them here, since this is the kind of detail that shows analytical rigor to anyone reviewing the repo.

## 7. Limitations

- The dataset covers a single year (2023) of order data and a limited set of cities and occasions, so findings should be read as illustrative of this dataset rather than as live business recommendations.
- Customer level behavioral data (e.g. repeat purchase history beyond what's in the dataset) was not available, limiting deeper retention analysis.
