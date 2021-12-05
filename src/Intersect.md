# Intersect

The INTERSECT operator returns only the rows that are common to the results of the two input queries.

<div style="text-align: center">
    <img alt="Intersect" src="./images/intersect.png" width="250" />
</div>

```sql
SELECT country, region, city FROM Employees
INTERSECT
SELECT country, region, city FROM Customers;
```

Instead of using the INTERSECT operator it is possible to use an alternative tool like an inner join or a correlated subquery, you need to add special treatment for NULLs—for example, assuming the alias E for Employees and C for


INTERSECT do not support ALL, but thanks to StackOverflow we can do that by ourself:

```sql
SELECT DISTINCT E.country, E.region, E.city
FROM Employees AS E
INNER JOIN Customers AS C
    ON E.region = C.region OR (E.region IS NULL AND C.region IS NULL)
```

