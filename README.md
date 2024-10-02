# SQL-Assignment-1
I have been hired as a Database Developer for a retail company that wants to enhance its customer and sales data management. My task is to design and implement a database to manage this information effectively. I will Follow the steps below to complete my assignment:

## Data Retrieval and Aggregation
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


SELECT c.CustomerID, SUM(s.quantity * p.price) AS total_spent
FROM sales s
JOIN products p 
ON s.ProductID = p.ProductID
INNER JOIN customers c ON s.CustomerID = c.CustomerID
GROUP BY c.CustomerID
ORDER BY total_spent DESC
LIMIT 1 ;

   - Write a query to find the total number of products sold in each category.

SELECT p.Category, SUM(s.Quantity) AS TotalSold 
FROM products p
JOIN sales s
ON s.productID = p.productID
GROUP BY p.Category


## Update and Delete Operations


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

5. Views:
   - Create a view named `CustomerSalesView` that shows the `CustomerID`, `FirstName`, `LastName`, and the total amount they have spent.
CREATE VIEW [CustomerSalesView ] 
SELECT CustomerID, FirstName, LastName


6. Joins and Advanced Queries:
   - Write a query to join `Customers` and `Sales` to display each customer's total number of purchases.

