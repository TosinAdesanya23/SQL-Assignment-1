# SQL-Assignment-1
I have been hired as a Database Developer for a retail company that wants to enhance its customer and sales data management. My task is to design and implement a database to manage this information effectively. I will Follow the steps below to complete my assignment:


## 1. Database and Table Creation:
---

### Create a database named `RetailDB`.
```
CREATE DATABASE RetailDB;
```

### In `RetailDB`, create the following tables:
 - `Customers`: To store customer information.

```
CREATE TABLE Customers (
CustomerID INT PRIMARY KEY,
FirstName VARCHAR(255),
LastName VARCHAR(255),
Email VARCHAR(255),
Phone INT
);
```
- `Products`: To store product information.

```
CREATE TABLE Products (
ProductID INT PRIMARY KEY,
ProductName VARCHAR (255),
Category VARCHAR(255),
Price DECIMAL (11,3)
);
```

 - `Sales`: To store sales transactions.
```
CREATE TABLE Sales (
SaleID INT PRIMARY KEY,
CustomerID INT FOREIGN KEY REFERENCES Customers(CustomerID),
ProductID INT FOREIGN KEY REFERENCES Products(ProductID),
SaleDate DATE,
Quantity INT,
TotalAmount DECIMAL(11, 3)
);

##  Data Retrieval and Aggregation
---
   
### Write a query to retrieve all customer information.

```
SELECT *
FROM Customers;
```

### Write a query to retrieve all product information.
```
SELECT *
FROM products;
```

### Write a query to list all sales transactions, including customer name and product name.

```
SELECT s.*, c.FirstName, c.LastName, p.ProductName
FROM sales s
JOIN customers c
ON s.customerid = c.CustomerID
JOIN products p
ON s.productID= p.productID ;
```

### Write a query to calculate the total sales amount for each product.

```
SELECT productid, SUM(totalamount) AS Total_Sales
FROM Sales
GROUP BY productID
```
 |productid| Total_Sales|
 |:--------|:-----------|
 |1       |        5000|
 |2       |       70007|
 |3       |        140|
 |4       |         50|
 |5       |        100|


### Write a query to find the customer who has spent the most money
```
Select customerid, SUM(totalamount) AS SumTotal
FROM customersalesview
GROUP BY customerid
ORDER BY SUM(totalamount)DESC
LIMIT 1

```
OR
```

SELECT c.customerID, SUM(s.TotalAmount) AS TotalSales
FROM customers c
JOIN Sales s
ON s.customerID = c.customerID
GROUP BY c.customerID
LIMIT 1
```

### Write a query to find the total number of products sold in each category.

```
SELECT ProductID, SUM(Quantity)
FROM Sales
GROUP BY ProductID
```

## Update and Delete Operations
---

### Write a query to update a customer’s email address

```
UPDATE customers
SET Email = 'topeadesanya@google.com'
WHERE CustomerID = 1; 
```

### Write a query to update the price of a product.

```
UPDATE products
SET Price = 10000.99
WHERE ProductID = 2
```

## Write a query to delete a specific sale transaction.
```
DELETE FROM Sales WHERE SaleID = 14
```

# Views
---
### Create Views syntax
```
CREATE VIEW view_name AS
Select column1, column2,...
FROM table_name
WHERE condition
```
### Create a view named `CustomerSalesView` that shows the `CustomerID`, `FirstName`, `LastName`, and the total amount they have spent.
```
CREATE VIEW CustomerSalesView AS
SELECT c.CustomerID, c.FirstName, c.LastName, s.totalamount
FROM Sales s
JOIN customers c
ON s.customerID = C.customerID

```


# Joins and Advanced Queries
---
   - Write a query to join `Customers` and `Sales` to display each customer's total number of purchases.

