# Restaurant Performance Analytics Dashboard

A data analysis and visualization project that transforms raw pizza sales data into actionable business insights using SQL and Power BI.

![Power BI](https://img.shields.io/badge/Power-BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Microsoft SQL Server](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft%20sql%20server&logoColor=white)
![SSMS](https://img.shields.io/badge/SSMS-CC2927?style=for-the-badge&logo=microsoft%20sql%20server&logoColor=white)

## Project Overview

This project involved an end-to-end analysis of pizza sales data to uncover trends and answer critical business questions. The process included data extraction and validation in **SQL Server Management Studio (SSMS)**, followed by the development of an interactive dashboard in **Microsoft Power BI**.

The final dashboard provides key metrics, performance trends, and a clear view of top and bottom-selling products, which can be used in data-driven decision-making for inventory planning, marketing strategies, and operational efficiency.

## Objectives

The primary goal was to analyze sales data to calculate essential KPIs and create visualizations for:
- **Business Performance Tracking:** Key metrics like Total Revenue, Average Order Value, and Total Orders.
- **Trend Analysis:** Identifying daily and monthly sales patterns to understand peak periods.
- **Product Analysis:** Determining the performance of pizza categories, sizes, and individual pizzas to identify best-sellers and underperformers.

## Technology Stack

- **Database & Tools:** Microsoft SQL Server, SQL Server Management Studio (SSMS)
- **BI & Visualization:** Microsoft Power BI, Power Query
- **Language:** SQL, DAX

## Key Insights & Findings

- **Total Revenue:** **$817,860.05**
- **Busiest Day:** **Friday** (3,538 orders)
- **Peak Sales Month:** **July** (1,935 orders)
- **Most Popular Category:** **Classic** (26.91% of total sales)
- **Most Popular Size:** **Large (L)** (45.89% of total revenue)
- **Average Order Value:** **$38.31**
- **Top-Selling Pizza:** **The Classic Deluxe Pizza** (by quantity and orders)

## Project Structure

```text
Pizza-Sales-Analysis/  
│  
├── Data/  
│   └── pizza_sales_data.xlsx  
│  
├── SQL Queries/  
│   ├── KPI and Chart Validation Scripts  
│   ├── 01_KPIs.sql  
│   ├── 02_Daily_Monthly_Trends.sql  
│   ├── 03_Sales_Distribution.sql  
│   └── 04_Top_Bottom_Performers.sql  
│  
├── Dashboard/  
│   └── Pizza_Sales_Report.pbix  
│  
└── [README.md]
```

## SQL Analysis

The project began with data exploration and validation in SSMS. SQL queries were written to calculate all required metrics and validate the data before importing into Power BI.

**Examples of KPIs calculated with SQL:**
```sql
-- Total Revenue
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;

-- Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;

-- Daily Trend for Total Orders
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales
GROUP BY DATENAME(DW, order_date);
```

## Power BI Dashboard Features

**The interactive dashboard includes:**

- **KPI Card:** Displaying Total Revenue, Average Order Value, Total Pizzas Sold, Total Orders, and Average Pizzas Per Order.
- **Trend Charts:** Bar and Line charts showing daily and monthly order trends.
- **Sales Distribution:** Donut charts for sales by category and size.
- **Product Performance:** Funnel chart for sales by category and interactive bar charts for the Top 5 and Bottom 5 pizzas by Revenue, Quantity, and Total Orders.

## How to Use

### Clone the repository:

```bash
git clone https://github.com/your-username/pizza-sales-analysis.git
```

### Database Setup:

1.  **Create Database**
    - **Prerequisites:** Ensure you have Microsoft SQL Server and SSMS installed.
    - Open **SQL Server Management Studio (SSMS)** and connect to your server.
    - Create a new database named `pizza_sales`
      
2. **Import the Excel Data:**

- Right-click on the new pizza_sales database in the Object Explorer.
- Navigate to Tasks > Import Data...
  - The SQL Server Import and Export Wizard will open. Click Next.
- Choose a Data Source:
  - Data source: Microsoft Excel
  - File path: Browse and select the pizza_sales_data.xlsx file from this repository's Data/ folder.
  - Ensure First row has column names is checked. Click Next.
- Choose a Destination:
  - Destination: Microsoft OLE DB Provider for SQL Server
  - Server name: Your local server (e.g., localhost or .)
- Database: pizza_sales. Click Next.

3.  **Connect Power BI:**
    - Open the `Dashboard/Pizza_Sales_Report.pbix` file in Power BI Desktop.
    - Go to `Transform data` > `Data source settings`.
    - Change the source to point to your local SQL Server instance and the `pizza_sales` database you just created.

4. **Interact with the Dashboard:**

  - Use the interactive elements to explore the data.

