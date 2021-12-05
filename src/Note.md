# Note

* The individual queries that are used as inputs to a set operator support all logical-query processing phases (such as table operators, WHERE, GROUP BY, and HAVING) except for ORDER BY. 
* Only the ORDER BY phase is allowed on the result of the operator.

```sql
SELECT country, COUNT(*) AS numlocations
FROM (SELECT country, region, city FROM Employees
      UNION
      SELECT country, region, city FROM Customers) AS U
GROUP BY country;
```

```sql
SELECT empid, orderid, orderdate
FROM (SELECT empid, orderid, orderdate
      FROM Orders
      WHERE empid = 3
      ORDER BY orderdate DESC, orderid DESC LIMIT 2) AS D1

UNION ALL

SELECT empid, orderid, orderdate
FROM (SELECT empid, orderid, orderdate
      FROM Orders
      WHERE empid = 5
      ORDER BY orderdate DESC, orderid DESC LIMIT 2) AS D2;
```