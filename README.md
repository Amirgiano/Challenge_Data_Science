# Data Science Intern Challenge
The Challenge is composed by two parts: 1. Spreadsheet Problem 2. SQL Problem
### Part 1: Spread Sheet
**On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis**
1. *Think about what could be going wrong with our calculation. Think about a better way to evaluate this data*
> The problem is actually accured because of the outliers in the distribution of the sales amount variables (because the quantity of the items were different. <br />
![image](https://user-images.githubusercontent.com/90762709/133863149-186fe7b2-35fd-4d33-a94a-a1839678fa02.png) <br />
As you see on the log distribution we have outliers(variables out of the upper/lower limits) in terms of the sales distribution. <br />
2. *What metric would you report for this dataset?* 
> The metrics to be used for this dataset is going to be the average per unit which we will obtain by **order_amount/total_items** and **averaging the value per unit**.
3. *What is its value?* <b />
> The new value is **387.74**
### Part 2: SQL
**For this question you’ll need to use SQL. Follow this [link](https://www.w3schools.com/SQL/TRYSQL.ASP?FILENAME=TRYSQL_SELECT_ALL) to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below**
1. *How many orders were shipped by Speedy Express in total?*
> `SELECT Shippers.ShipperName, COUNT(Orders.OrderID) as Order_number` <br />
`FROM Orders` <br />
`LEFT JOIN Shippers ON Orders.ShipperID==Shippers.ShipperID` <br />
`WHERE ShipperName=="Speedy Express"` <br /><br />
![image](https://user-images.githubusercontent.com/90762709/133861949-97dd3128-13a1-4892-9534-c107768cad8d.png)<br /><br />
The answer is **54**
2. *What is the last name of the employee with the most orders?* 
>`SELECT Employees.LastName, COUNT(Orders.OrderID) as Order_number` <br />
`FROM Orders` <br />
`JOIN Employees ON Employees.EmployeeID== Orders.EmployeeID` <br />
`GROUP BY LastName`	 <br />
`ORDER BY Order_number DESC;` <br /> <br />
![image](https://user-images.githubusercontent.com/90762709/133862245-000dcc58-55d3-49c8-8c6a-429db4431e4f.png)<br /><br />
The answer is **Peacock**
3. *What product was ordered the most by customers in Germany?*
> `SELECT Products.ProductName, SUM(OrderDetails.Quantity) as Amount, Customers.Country` <br />
`FROM OrderDetails` <br /> 
`JOIN Products` <br />
`ON Products.ProductID==OrderDetails.ProductID` <br /><br />
`JOIN Orders` <br />
`ON Orders.OrderID==OrderDetails.OrderID` <br /><br />
`JOIN Customers` <br />
`ON Orders.CustomerID == Customers.CustomerID` <br /><br />
`WHERE Customers.Country=="Germany"`<br />
`GROUP BY ProductName`<br />
`ORDER BY Amount DESC` <br /><br />
![image](https://user-images.githubusercontent.com/90762709/133862578-0256afc6-69e0-4e7d-9ead-d9a582ac9e0a.png) <br /><br />
The answer is **Boston Crab Meat**

### Additional: 
I wondered what if we had no the quantity of items next to the sales amount? <br />
For this case I have tried to find the quartiles, define lower and upper limits and remove outliers: <br /> <br /> 
![image](https://user-images.githubusercontent.com/90762709/133862814-eb733f52-c6bc-4225-ad11-0c10b5acf662.png)<br /> 
These are the quartiles and the upper/lowe limit: We are mainly interested in upper limit. By using the formula **AVERAGEIF()** we exclude the upper limit and here what we get.  <br />
![image](https://user-images.githubusercontent.com/90762709/133862958-1b83269b-d7b5-4a8c-8147-573cb17a7fb8.png) <br /><br />
And here is the final summary of what we had discovered. <br /> <br />

![image](https://user-images.githubusercontent.com/90762709/133863095-0e903a69-e9f0-4b40-8acf-1134be87565c.png)<br />
Thank you! 




