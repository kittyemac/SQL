## Create a grocery store database

```sql
CREATE TABLE store (id INTEGER PRIMARY KEY, item TEXT, section TEXT, price INTEGER, popularity INTEGER);
```
```sql
INSERT INTO store VALUES (1, "porridge oats", "produce", 2.49, 2);
INSERT INTO store VALUES (2, "strawberry jam", "produce", 3.15, 5);
INSERT INTO store VALUES (3, "mango", "frozen", 2.79, 3);
INSERT INTO store VALUES (4, "soy milk", "dairy and alternatives",1.89,5);
INSERT INTO store VALUES (5, "dates", "fresh", 5.01, 6);
INSERT INTO store VALUES (6, "bananas", "fresh", 2.09, 7);
INSERT INTO store VALUES (7, "limes", "fresh", 0.19, 4);
INSERT INTO store VALUES (8, "cooking apples", "fresh", 3.63, 5);
INSERT INTO store VALUES (9, "spaghetti", "produce", 2.16, 8);
INSERT INTO store VALUES (10, "spirulina", "health foods", 6.89, 3);
INSERT INTO store VALUES (11, "omega-3", "vitamins", 5.69, 2);
INSERT INTO store VALUES (12, "eggs", "produce", 2, 6);
INSERT INTO store VALUES (13, "dog food", "pets", 5.50, 8);
INSERT INTO store VALUES (14, "kiwi fruit", "fresh", 3.80, 3);
INSERT INTO store VALUES (15, "power paste", "household", 1.90, 4);
```
### display the database ordered by price. 
```sql
SELECT * FROM store
ORDER BY price desc;
```

### what is the average price of items in the fresh section? 
```sql
SELECT AVG(price) "avg fresh item price"
FROM store
WHERE section = "fresh";
```

### what are the six most popular items? 
```sql
SELECT item, price, popularity
FROM store
ORDER BY popularity desc
LIMIT 6;
```
