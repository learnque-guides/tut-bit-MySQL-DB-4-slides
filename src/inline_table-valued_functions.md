# Inline table-valued functions

Derived tables and CTEs have a single-statement scope, which means they are not reusable. Inline TVFs are reusable table expressions that support input parameters.

```sql
DROP FUNCTION IF EXISTS GetCustOrders
GO
CREATE FUNCTION GetCustOrders
    (@cid AS INT) RETURNS TABLE
AS
RETURN
    SELECT orderid, custid, empid, orderdate, 
        requireddate, shippeddate, shipperid, 
        freight, shipname, shipaddress, shipcity, 
        shipregion, shippostalcode, shipcountry
    FROM Orders
    WHERE custid = @cid
```