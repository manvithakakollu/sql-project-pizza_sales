# sql-project-pizza_sales
used sql 
#Taken the data from kaggle pizza data used to 
#find the hourly based and weekly based revenue
use pizza_sales
select * from pizza_sales
select sum(total_price) as total_billamount from pizza_sales
select count(Distinct order_id)  as countof_id from pizza_sales
select sum(total_price)/count(Distinct order_id) as avg_order_value from pizza_sales
select sum(quantity) as Total_pizza_sold from pizza_sales
select cast(sum(quantity) As Decimal(10,2))/count(Distinct order_id) As Avg_pizzas_per_order from pizza_sales
#Daily trent chart 
select DATENAME(DW,order_date) as order_day,count(Distinct order_id) As Total_orders
from pizza_sales
group by Datename(DW,order_date)
#Hourly trend
select Datepart(hour,Order_time) as order_hours,count(Distinct order_id) As Total_orders
from pizza_sales
group by Datepart(hour,Order_time)
order by Datepart(hour,Order_time)
#sales  with pizzatype

select pizza_category,sum(total_price)*100/(select sum(total_price) from pizza_sales)
from pizza_sales 
group by pizza_category
