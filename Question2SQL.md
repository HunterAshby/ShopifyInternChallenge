# Question 2
### a. How many orders were shipped by Speedy Express in total?
#### Answer 54
Query:\
`SELECT COUNT(*)`\
`FROM Shippers`\
`INNER JOIN Orders`\
`ON Shippers.ShipperID = Orders.ShipperID`\
`WHERE ShipperName = "Speedy Express"`
### b. What is the last name of the employee with the most orders
#### Answer Peacock, 40 Orders
Query:\
`SELECT LastName, MAX(OrderCount)`\
`From (`\
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`SELECT COUNT(*) AS OrderCount, LastName`\
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`FROM Orders`\
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`INNER JOIN Employees`\
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`ON Orders.EmployeeID = Employees.EmployeeID`\
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`GROUP BY Orders.EmployeeID)`
### c. What product was ordered the most by customers in Germany?
#### Answer Boston Crab Meat, 160 Orders
Query:\
`SELECT ProductName, MAX(ProductSum)`\
`From(`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`SELECT ProductName, SUM(Quantity) AS ProductSum, Country`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`FROM Orders`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`INNER JOIN Customers`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`ON Orders.CustomerID = Customers.CustomerID`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`INNER JOIN OrderDetails`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`ON Orders.OrderID = OrderDetails.OrderID`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`INNER JOIN Products`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`ON OrderDetails.ProductID = Products.ProductID`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Where Country == "Germany"`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`GROUP BY ProductName)`
