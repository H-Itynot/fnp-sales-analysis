# Ferns & Petals (FNP) Sales Analysis Dashboard

An end to end Excel analytics project that cleans, models, and visualizes gifting and floral order data for FNP (Ferns & Petals), a company that delivers gifts and flowers for occasions such as Diwali, Raksha Bandhan, Holi, Valentine's Day, Birthdays, and Anniversaries.

![Dashboard Preview](screenshots/dashboard_overview.png)

## Problem Statement

FNP needed visibility into sales trends, customer behavior, and product performance to improve sales strategy and customer satisfaction. The analysis was scoped around ten business questions:

1. What is the overall revenue
2. What is the average order to delivery time
3. How do monthly sales fluctuate across 2023
4. Which products generate the most revenue
5. How much do customers spend on average
6. How do the top 5 products perform over time
7. Which 10 cities place the highest number of orders
8. Does order quantity affect delivery time
9. How does revenue compare across occasions
10. Which products are most popular for specific occasions

## Executive Summary

Across the dataset, FNP recorded **1,000 total orders** from **100 customers**, generating **₹3,520,984 in total revenue**, with an average customer spend of **₹3,520.98** and an average order to delivery time of **5.53 days**.

Key findings from the dashboard:

- **Occasion mix drives revenue concentration.** Anniversary, Holi, and Raksha Bandhan are the strongest revenue occasions, while Diwali and Valentine's Day trail behind, suggesting an opportunity to run targeted promotions around the lower performing occasions.
- **Category performance is uneven.** The Colors category is the single largest revenue driver, with Soft Toys and Sweets as secondary contributors. Mugs and Plants generate comparatively little revenue, which may warrant a review of pricing, placement, or marketing for those categories.
- **Order timing follows a daily rhythm.** Revenue by hour shows clear peaks in the evening hours, which is useful for timing promotions, ad spend, and customer support staffing.
- **Sales are seasonal.** Monthly revenue spikes sharply around February and August, with a smaller rise toward November, likely tied to occasion calendars (e.g. Valentine's season, Raksha Bandhan, and pre festive demand).
- **A small set of products carries outsized revenue.** Among the top 5 products by revenue, the Magnum Set leads, with Dolores Gift and Quia Gift as strong secondary performers.
- **Order volume is geographically spread but uneven.** Cities like Imphal and Kavali lead the top 10 cities by order count, indicating regional demand pockets worth deeper investment.

## Dashboard Features

- KPI summary cards (Total Customers, Total Orders, Total Revenue, Order-Delivery Time, Avg Customer Spending)
- Revenue by Occasion, Category, Hour of Day, and Month
- Top 5 Products by Revenue
- Top 10 Cities by Number of Orders
- Interactive slicers for Order Date, Delivery Date, and Occasion, allowing dynamic filtering across all visuals

## Tools and Techniques

- **Power Query** for data cleaning, transformation, and shaping the source tables before loading
- **Power Pivot** for building the data model and relationships between tables
- **DAX measures** for calculated KPIs such as Total Revenue, Average Order to Delivery Time, and Average Customer Spending
- **PivotTables and PivotCharts** connected to the data model for all visualizations
- **Slicers** for interactive, cross-filterable dashboard navigation

## Repository Structure

```
fnp-sales-analysis/
├── README.md
├── METHODOLOGY.md
├── data/
│   └── fnp_sales_dataset.csv
├── screenshots/
│   └── dashboard_overview.png
└── FNP_Sales_Dashboard.xlsx
```

## Dataset

A publicly available, simulated dataset modeling FNP style gifting and floral orders, split across three tables:

- **customers.csv** — 100 rows (Customer ID, Name, City, Contact Number, Email, Gender, Address)
- **orders.csv** — 1,000 rows (Order ID, Customer ID, Product ID, Quantity, Order Date, Order Time, Delivery Date, Delivery Time, Location, Occasion)
- **products.csv** — 70 rows (Product ID, Product Name, Category, Price, Occasion)

See `data/` for the raw files and `METHODOLOGY.md` for how they were cleaned and modeled.

## Notes

This project was completed as a self-directed portfolio exercise to demonstrate Excel based data analysis, data modeling, and dashboard design skills, including Power Query, Power Pivot, DAX, and interactive PivotChart based reporting.
