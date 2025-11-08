# DAX-Data-Visualization
E-Commerce Sales Analysis — Power BI Project
Overview

This project focuses on analyzing e-commerce sales data using Power BI.
You will explore sales trends, profitability, and target achievement by applying Data Modeling, DAX (Data Analysis Expressions), and interactive visualizations.

 Objective

To transform and analyze sales data from multiple sources, calculate key business metrics, and build insightful dashboards that reveal trends and performance across categories, time, and regions.

 Dataset Files

You will work with the following CSV files:

List of Orders.csv — Contains customer and order information (Order ID, Order Date, Customer, City, State, etc.).

Order Details.csv — Includes product-level details such as Category, Sub-Category, Quantity, Amount, and Profit.

Sales Target.csv — Contains monthly and category-wise sales targets.

 1. Data Modeling

Before visualization, data modeling must be completed to ensure relational integrity and accurate calculations.

Steps:

Import all three CSV files into Power BI.

Establish the following relationships:

List of Orders ↔ Order Details — via Order ID

Order Details ↔ Sales Target — via Category

Ensure all relationships are active and in the correct cardinality (typically one-to-many).

Confirm data types for numeric, date, and text fields.

 2. Calculated Columns (Using DAX)
 a) Category Type

Create a new column in the Order Details table that combines Category and Sub-Category:

Category Type = [Category] & " - " & [Sub-Category]

b) Revenue per Order

Compute revenue per order as the product of Amount and Quantity:

Revenue per Order = [Amount] * [Quantity]

c) Sales Category

Categorize each order based on whether its Amount is above or below the average:

Sales Category =
IF([Amount] > AVERAGE('Order Details'[Amount]), "Above Average", "Below Average")


Outcome:
Enhanced data granularity for analyzing performance by category, order, and sales strength.

 3. Calculated Measures (Using DAX)
 a) Order Count

Measure the total number of orders:

Order Count = DISTINCTCOUNT('Order Details'[Order ID])

 b) Average Profit in Delhi

Calculate the average profit for orders placed in Delhi:

Average Profit (Delhi) =
CALCULATE(
    AVERAGE('Order Details'[Profit]),
    'List of Orders'[City] = "Delhi"
)

c) Year-to-Date (YTD) Sales

Compute the cumulative sales from the start of the year to the current order date:

YTD Sales =
TOTALYTD(
    SUM('Order Details'[Amount]),
    'List of Orders'[Order Date]
)


Outcome:
Key KPIs ready for use in visual dashboards to monitor sales and profitability performance.

4. Data Visualization
a) Sales Target Achievement by Category

Chart Type: Clustered Column Chart

Fields:

Axis → Category

Value → Total Sales (Amount)

Target → Sales Target

Insight: Compare actual vs. target sales by category.

 b) Max Profit Margin by Sub-Category

Chart Type: Donut Chart

Fields:

Legend → Sub-Category

Values → Max(Profit Margin)

Insight: Identify the sub-categories with the highest profit margins.

 c) Monthly Sales Trend

Chart Type: Line Chart

Fields:

X-Axis → Order Date (Month)

Y-Axis → Total Sales (Amount)

Insight: Analyze month-over-month sales performance.

 d) Profit vs. Quantity Comparison

Chart Type: Scatter Chart

Fields:

X-Axis → Quantity

Y-Axis → Profit

Details → Sub-Category

Insight: Identify which sub-categories generate high profits relative to quantity sold.

 e) Sales vs. Target Cards

Visuals:

Card 1: Total Sales Amount

Card 2: Total Sales Target

Multi-row Card: Minimum Target by Segment

Insight: Quickly compare current performance to assigned targets.

 f) Sales Performance Matrix

Chart Type: Matrix

Fields:

Rows → Category

Columns → Month (Order Date)

Values → Actual Sales and Sales Target

Insight: Monitor how sales vary across categories and time periods compared to targets.

g) Geographic Sales Analysis

Chart Type: Map

Fields:

Location → City

Values → Total Sales Amount

Insight: Visualize regional sales performance and identify top-performing cities.

 h) Sales Distribution by Sub-Category

Chart Type: Treemap

Fields:

Group → Sub-Category

Values → Total Sales Amount

Insight: Understand the proportional contribution of each sub-category to total sales.

 i) Order Count Analysis by State

Chart Type: Funnel Chart

Fields:

Category → State

Values → Order Count

Insight: Compare the number of orders across different states in a ranked visual.
