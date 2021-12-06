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

The *UNION* operator has several limitations:

* The output is labeled with the names of the columns or expressions from the first query. Use column aliases to change this behavior.
* The queries must output the same number of columns. If you try using different numbers of columns, MySQL will report an error.
* All matching columns must have the same type. So, for example, if the first column output from the first query is a date, the first column output from any other query must also be a date.
* The results returned are unique, as if you’d applied a *DISTINCT* to the overall result set.

You can use *UNION ALL* if you do not want to have *DISTINCT* behiavour.

If you know that two tables do not contains duplicate records it is better to use `UNION ALL` for performance

Note: The output of a *UNION* operation isn’t guaranteed to be ordered even if the subqueries are ordered, so if you want the final output to be ordered, you should add an ORDER BY clause at the end of the whole query.
