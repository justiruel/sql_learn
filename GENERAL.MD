## CONCAT

SQL Server 2012:
```
SELECT CONCAT(first_name,' ',last_name) as nama from customer
```

Under SQL Server 2012:

```
SELECT (first_name+' '+last_name) as nama from customer
```
