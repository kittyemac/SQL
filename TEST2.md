### In this SQL, I'm querying a database with multiple tables in it to quantify statistics about customer and order data.

```sql
SELECT COUNT(orderid)
FROM BIT_DB.JanSales
WHERE length(orderid) = 6
AND orderid <> 'Order ID’;
```
