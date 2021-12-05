# Exercise 3

Write a query that returns rows with row numbers 11 through 20 based on the row-number definition:

```sql
SELECT orderid, orderdate, custid, empid, @i := @i+1 AS rownum 
FROM Orders, (SELECT @i := 0) AS f;
```

* Table involved: Orders
* Output:

```sql
orderid     orderdate   custid      empid       rownum
----------- ----------- ----------- ----------- -------
10258       2014-07-17  20          1           11
10259       2014-07-18  13          4           12
10260       2014-07-19  56          4           13
10261       2014-07-19  61          4           14
10262       2014-07-22  65          8           15
10263       2014-07-23  20          9           16
10264       2014-07-24  24          6           17
10265       2014-07-25  7           2           18
10266       2014-07-26  87          3           19
10267       2014-07-29  25          4           20

(10 row(s) affected)
```
