# Precedence

SQL defines precedence among set operators. The INTERSECT operator precedes UNION and EXCEPT, and UNION and EXCEPT are evaluated in order of appearance.

```sql
SELECT country, region, city FROM Suppliers
EXCEPT
SELECT country, region, city FROM Employees
INTERSECT
SELECT country, region, city FROM Customers;
```

To control the order of evaluation of set operators, use parentheses, because they have the highest precedence.
