# InternshipChallenge-2022




## Ques 1) The detailed python file can be found here: 






## QUESTION 2 : USING SQL
Ques 1) How many orders were shipped by Speedy Express in total? 

# Code:

select count(*) from 
(select * from Orders o join shippers s on o.ShipperID = s.ShipperID) 
where ShipperName = 'Speedy Express'
### Answer -> 54
Ques 2) What is the last name of the employee with the most orders?

# Code: 

select LastName from Employees 
where EmployeeID in 
(select EmployeeID from (SELECT EmployeeID, 
count(OrderID) as orders FROM [Orders] group by 
EmployeeID) order by orders DESC limit 1)

### Answer -> Peacock
Ques 3) What product was ordered the most by customers in Germany?

#Code: 
SELECT pd_details.ProductName,sum(Quantity) as product_quantity FROM Orders o Join 
(select CustomerID,Country from Customers) cs 
on o.CustomerID=cs.CustomerID Join 
OrderDetails od on 
o.OrderID = od.OrderID join
Products pd_details on 
od.ProductID = pd_details.ProductID 
group by pd_details.ProductName order by product_quantity DESC limit 1

### Answer -> Gorgonzola Telino . The same was ordered 458 times



