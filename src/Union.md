# Union

The UNION operator unifies the results of two input queries. If a row appears in any of the input sets, it will appear in the result of the UNION operator. SQL supports both the UNION ALL and UNION (implicit DISTINCT) flavors of the UNION operator.

<div style="text-align: center">
    <img alt="Union" src="./images/union.png" width="250" />
</div>

```sql
SELECT country, region, city FROM Employees
UNION
SELECT country, region, city FROM Customers;

SELECT country, region, city FROM Employees
UNION ALL
SELECT country, region, city FROM Customers;
```

If you know that two tables do not contains duplicate records it is better to use `UNION ALL` for performance
