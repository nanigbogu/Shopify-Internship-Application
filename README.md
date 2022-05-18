# Shopify-Internship-Application

# Question 1

a. Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

**The average order value is calculated by taking the total revenue and dividing it by the total amount of orders. In the scenario, it was calculated correctly but there was no effort to evaluate the data without outliers.**

b. What metric would you report for this dataset?

**I would report the order amount to calculate the average order value.**

c. What is its value?

**Without outliers, the average order value is $299.68.**

# Question 2

1. How many orders were shipped by Speedy Express in total?

**54 orders were shipped by Speedy Express**

SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS no_orders
FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;

2. What is the last name of the employee with the most orders?

**EmployeeID: 4 has 40 orders. This person's last name is *Peacock*.**

SELECT Employees.LastName, COUNT(Orders.OrderID) As no_orders 
FROM Orders
Left JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
GROUP BY LastName Order by no_orders Desc
LIMIT 1;

3. What product was ordered the most by customers in Germany?

**Boston Crab Meat**

SELECT p.productName, COUNT(p.productID)
FROM products p, customers c, orders o, orderdetails od
WHERE c.country = 'Germany'
AND  o.customerID = c.customerID
AND o.orderID = od.orderID
AND od.productID = p.productID;