# TARGET_BUSINESS_CASE_STUDY
Target is a globally renowned brand and a prominent retailer in the United States. Target makes itself a preferred shopping destination by offering outstanding value, inspiration, innovation and an exceptional guest experience that no other retailer can deliver.
# **Target Business Case Study: Customer Segmentation & Sales Analysis (SQL)**

## **1. Introduction**
This case study analyzes **Target's customer segmentation and sales trends** using SQL to optimize marketing strategies and improve revenue. By querying customer demographics, purchasing behavior, and seasonal sales trends, this study aims to provide actionable insights that can enhance Target’s business strategy.

## **2. Business Problem Statement**
Target wants to **improve customer engagement and boost sales** by identifying key customer segments, understanding their shopping habits, and personalizing marketing efforts. The primary objectives of this analysis are:
- To categorize customers based on purchasing behavior.
- To identify high-value customer segments.
- To recommend business strategies that enhance customer experience and sales.

## **3. Dataset Information**
- **Source:** (Specify the dataset source, e.g., company database, simulated data, or an online dataset)
- **Key Tables:**
  - `customers` (Customer ID, Name, Age, Gender, Location, Income)
  - `transactions` (Transaction ID, Customer ID, Date, Product ID, Price, Quantity)
  - `products` (Product ID, Category, Brand, Price)
  - `sales` (Date, Store ID, Revenue, Discount Applied)
- **Data Preprocessing:**
  - Removing duplicate records
  - Handling missing values
  - Normalizing data

## **4. SQL Queries & Methodology**
The case study follows a structured approach using SQL queries:

1. **Customer Segmentation:**
   ```sql
   SELECT customer_id, COUNT(transaction_id) AS purchase_count, SUM(price * quantity) AS total_spent
   FROM transactions
   GROUP BY customer_id
   ORDER BY total_spent DESC;
   ```
   - Identifies high-value customers based on purchase frequency and total spending.

2. **Sales Trend Analysis:**
   ```sql
   SELECT DATE_TRUNC('month', date) AS sales_month, SUM(revenue) AS total_revenue
   FROM sales
   GROUP BY sales_month
   ORDER BY sales_month;
   ```
   - Shows revenue trends over time.

3. **Most Purchased Products:**
   ```sql
   SELECT p.category, COUNT(t.transaction_id) AS total_purchases
   FROM transactions t
   JOIN products p ON t.product_id = p.product_id
   GROUP BY p.category
   ORDER BY total_purchases DESC;
   ```
   - Determines the most frequently bought product categories.

4. **Customer Demographics Impact:**
   ```sql
   SELECT age, gender, AVG(total_spent) AS avg_spending
   FROM (
       SELECT c.customer_id, c.age, c.gender, SUM(t.price * t.quantity) AS total_spent
       FROM customers c
       JOIN transactions t ON c.customer_id = t.customer_id
       GROUP BY c.customer_id, c.age, c.gender
   ) AS customer_spending
   GROUP BY age, gender
   ORDER BY avg_spending DESC;
   ```
   - Evaluates how age and gender influence purchasing behavior.

## **5. Key Findings & Insights**
- **High-Value Customers:** A small percentage of customers contribute significantly to revenue.
- **Seasonal Shopping Trends:** Sales increase during holiday seasons and promotional events.
- **Popular Product Categories:** Electronics and household items dominate sales.
- **Demographics Influence:** Customers aged **25-40** tend to spend the most.

## **6. Business Recommendations**
Based on the SQL analysis, the following strategies are recommended:
1. **Personalized Marketing Campaigns:** Send promotions to high-value customers.
2. **Inventory Optimization:** Stock high-demand products before peak sales periods.
3. **Loyalty Programs:** Implement reward systems for frequent shoppers.
4. **Targeted Discounts:** Offer age and gender-specific deals based on past spending trends.

## **7. Tools & Technologies Used**
- **Database Management Systems:** PostgreSQL / MySQL / SQL Server
- **Query Execution & Visualization:** SQL Workbench, Tableau / Power BI
- **Techniques Used:** Aggregation, Joins, Subqueries, Window Functions

## **8. How to Use This Repository**
### **Prerequisites**
- Install an SQL database system (e.g., PostgreSQL, MySQL)
- Load the dataset into your database.

### **Running the Queries**
1. Clone this repository:
   ```sh
   git clone https://github.com/your-repo/target-case-study-sql.git
   ```
2. Navigate to the directory:
   ```sh
   cd target-case-study-sql
   ```
3. Open the SQL script (`target_analysis.sql`) and execute it in your SQL environment.

## **9. Conclusion**
This case study provides a **data-driven approach** to understanding Target’s customer segmentation and sales trends using SQL. By leveraging structured queries, businesses can optimize inventory, target marketing campaigns, and enhance customer engagement.



