# SQL-Projects

# E-Commerce Database Project

## Overview
This project implements a relational database for an e-commerce platform. It includes tables for customers, products, orders, order items, and customer feedback. The database is designed to handle basic e-commerce operations and provide insights through various SQL queries.

## Database Schema

The database consists of the following tables:

1. `Customers`: Stores customer information
2. `Products`: Contains product details
3. `Orders`: Tracks customer orders
4. `OrderItems`: Links orders with products and quantities
5. `Feedback`: Stores customer feedback on products

## Key Features

- Customer management
- Product inventory
- Order processing
- Customer feedback and ratings
- Data archiving for old orders

## SQL Scripts

The project includes the following types of SQL scripts:

1. Table creation scripts
2. Data insertion scripts
3. Query scripts for data retrieval and analysis
4. Data manipulation scripts (e.g., updating product prices)
5. Data archiving scripts

## How to Use

1. Set up a SQL database system (e.g., SQLite, MySQL, PostgreSQL).
2. Run the table creation scripts to set up the database structure.
3. Use the insertion scripts to populate the tables with sample data.
4. Execute the provided queries to interact with the data and gain insights.

## Example Queries

1. Retrieve all feedback ratings above 4:
   ```sql
   SELECT customer_id, feedback_text, rating, feedback_date
   FROM Feedback
   WHERE rating >= 4
   ORDER BY rating ASC;
   ```

2. Calculate total sales:
   ```sql
   BEGIN TRANSACTION;
   CREATE TEMP TABLE InvoicePrice AS
   SELECT
   oi.order_id,
   p.product_name,
   p.price,
   oi.quantity,
   (p.price * oi.quantity) AS total_cost
   FROM OrderItems oi
   INNER JOIN Products p ON oi.product_id = p.product_id;
   SELECT SUM(total_cost)
   FROM InvoicePrice;
   COMMIT;
   ```

3. Archive orders over a year old:
   ```sql
   BEGIN TRANSACTION;
   -- (See full script in the project files
