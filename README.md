# Data Science Intern Challenge
The Challenge is composed by two parts: 1. Spreadsheet Problem 2. SQL Problem
### Part 1: Spread Sheet
**On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis**
1. *Think about what could be going wrong with our calculation. Think about a better way to evaluate this data*
> The problem is actually accured because of the outliers in the distribution of the sales amount variables (because the quantity of the items were different. <br />
![Distribution Histogram](https://raw.githubusercontent.com/Amirgiano/Challenge_data_scientist/main/SalesDist.png) <br />
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
![image](https://user-images.githubusercontent.com/90762709/133861949-97dd3128-13a1-4892-9534-c107768cad8d.png)
2. *What is the last name of the employee with the most orders?* 
>`SELECT Employees.LastName, COUNT(Orders.OrderID) as Order_number` <br />
`FROM Orders` <br />
`JOIN Employees ON Employees.EmployeeID== Orders.EmployeeID` <br />
`GROUP BY LastName`	 <br />
`ORDER BY Order_number DESC;` <br />
![image](https://user-images.githubusercontent.com/90762709/133862245-000dcc58-55d3-49c8-8c6a-429db4431e4f.png)

