# Views

Derived tables and CTEs have a single-statement scope, which means they are not reusable. Views are stored as permanent objects in the database, making them reusable.

```sql
DROP VIEW IF EXISTS USACusts;
GO
CREATE VIEW USACusts
AS
SELECT
  custid, companyname, contactname, contacttitle, address,
  city, region, postalcode, country, phone, fax
FROM Customers
WHERE country = 'USA';
```

## The SCHEMABINDING option (only for MSSQL)

The SCHEMABINDING option is available to views and it binds the schema of referenced objects and columns to the schema of the referencing object.

You will not be able to rmeove any column from schema that you binded to

```sql
ALTER VIEW USACusts WITH SCHEMABINDING
AS
-- Will not be able to drop address, city and ect.
SELECT
  custid, companyname, contactname, contacttitle, address,
  city, region, postalcode, country, phone, fax
FROM Customers
WHERE country = 'USA';
GO
```

To support the *SCHEMABINDING* option - the query is not allowed to use `*` in the SELECT clause. You have to explicitly list column names.