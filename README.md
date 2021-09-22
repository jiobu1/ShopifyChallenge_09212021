# Shopify

## Question 1
**Question 1:** Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis.

- a. Think about what could be going wrong with our calculation. Think about a better way to evaluate this data.
- b. What metric would you report for this dataset?
- c. What is its value?

**Answers**
- 1a. What was wrong with the calculation is that stores #42 and #77 skew the numbers.
- 1b. The easiest metric would be to find the median of all the sales.
- 1c. The sales number that I got was $284.0.


## Question 2
**Question 2:** For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

- a. How many orders were shipped by Speedy Express in total? 
- b. What is the last name of the employee with the most orders?
- c. What product was ordered the most by customers in Germany?

**Answers**
2a. The total number orders by Speedy Express is 54
``SELECT COUNT(*)``
``FROM Orders``
``WHERE ShipperID = 1``


2b. The employee with the most orders is Peacock
``(select EmployeeID, COUNT(EmployeeID) AS MOST_FREQUENT``
``from Orders``
``GROUP BY EmployeeID``
``ORDER BY COUNT(EmployeeID) DESC)``

The above query yields a table that groups order totals by Employee ID. I had to cross reference the EmployeeID that came up first
which was EmployeeID with 40 orders with the Employees table

2c.
``SELECT Products.ProductName, Customers.Country``
``FROM Customers``
``RIGHT JOIN Orders on Customers.CustomerID = Orders.CustomerID``
``RIGHT JOIN OrderDetails on Orders.OrderID = OrderDetails.OrderID``
``RIGHT JOIN Products ON OrderDetails.ProductID = Products.ProductID``
``WHERE Country = 'Germany'``
``GROUP BY ProductName Desc;``

This is as far as I got with this question. I understand that I need to join the CustomerID, OrderID, ProductIDs from Products,
Customers, OderDetails, and Orders. I wanted to make sure that ProductName and Country were included to make it easier to see visually
but unfortunatetly I got the error ``Syntax error (missing operator)``.

