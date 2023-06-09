### In this SQL, I'm querying a database with multiple tables in it to quantify statistics about customer and order data.

**1. How many orders were placed in January?**

```sql
SELECT COUNT(orderid)
FROM BIT_DB.JanSales
WHERE length(orderid) = 6
AND orderid <> 'Order ID’;
```

**2. How many of those orders were for an iPhone?**

```sql
SELECT COUNT(orderid) 
FROM BIT_DB.JanSales
WHERE Product = 'iPhone'
AND length(orderid) = 6
AND orderid <> 'Order ID';
```

**3. Select the customer account numbers for all the orders that were placed in February.**

```sql
SELECT distinct acctnum
FROM BIT_DB.customers cust

INNER JOIN BIT_DB.FebSales feb
ON cust.order_id=feb.orderid 
WHERE length(orderid) = 6 
AND orderid <> 'Order ID’;
```

**4. Which product was the cheapest one sold in January, and what was the price?**

```sql
SELECT product, MIN(price)
FROM BIT_DB.JanSales
GROUP BY product, price
ORDER BY price asc
LIMIT 1;
```

**5. What is the total revenue for each product sold in January?**

```sql
SELECT product, SUM(quantity) * price as revenue
FROM BIT_DB.JanSales
WHERE length(orderid) = 6
GROUP BY product;
```

**6. Which products were sold in February at 548 Lincoln St, Seattle, WA 98101, how many of each were sold, and what was the total revenue?**

```sql
SELECT product, quantity, SUM(quantity) * price as revenue
FROM BIT_DB.FebSales
WHERE location = '548 Lincoln St, Seattle, WA 98101'
GROUP BY product;
```

**7. How many customers ordered more than 2 products at a time in February, and what was the average amount spent for those customers?**

```sql
SELECT count(distinct cust.acctnum) as cust_count, AVG(quantity * price) as avg_revenue
FROM BIT_DB.FebSales Feb
LEFT JOIN BIT_DB.customers cust
ON Feb.orderid = cust.order_id
WHERE Feb.Quantity > 2
AND length(orderid) = 6
AND orderid <> 'Order ID';
```

**8. List all the products sold in Los Angeles in February, and include how many of each were sold.**

```sql
SELECT distinct product, SUM(quantity) AS quantity_sold
FROM BIT_DB.FebSales
WHERE location like '%Los Angeles%'
GROUP BY product;
```

**9. Which locations in New York received at least 3 orders in January, and how many orders did they each receive?**

```sql
SELECT distinct location, COUNT(orderid)
FROM BIT_DB.JanSales
WHERE location like '%NY%'
AND length(orderid) = 6 
AND orderid <> 'Order ID'
GROUP BY location
HAVING count(orderID)>2;
```

**10. How many of each type of headphone were sold in February?**

```sql
SELECT distinct product, SUM(quantity) AS quantity
FROM BIT_DB.FebSales
WHERE product like '%headphones%'
AND length(orderid) = 6 
AND orderid <> 'Order ID'
GROUP BY product;
```

**11. What was the average amount spent per account in February?**

```sql
SELECT AVG(quantity * price) AS avg_spend
FROM BIT_DB.FebSales Feb

LEFT JOIN BIT_DB.customers cust
ON Feb.orderID = cust.order_id

WHERE length(orderid) = 6 
AND orderid <> 'Order ID';
```

**12. What was the average quantity of products purchased per account in February?**

```sql
SELECT SUM(quantity)/COUNT(cust.acctnum) AS avg_quant
FROM BIT_DB.FebSales Feb

LEFT JOIN BIT_DB.customers cust
ON Feb.orderID = cust.order_id

WHERE length(orderid) = 6 
AND orderid <> 'Order ID';
```

**13. Which product brought in the most revenue in January and how much revenue did it bring in total?**

```sql
SELECT product, SUM(quantity * price) AS rev
FROM BIT_DB.JanSales 
GROUP BY product
ORDER BY SUM(quantity * price) desc
LIMIT 1;
```
