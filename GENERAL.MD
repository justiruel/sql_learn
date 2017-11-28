## CONCAT

SQL Server 2012:
```
SELECT CONCAT(first_name,' ',last_name) as nama from customer
```

Under SQL Server 2012:

```
SELECT (first_name+' '+last_name) as nama from customer
```

## ISNULL

```
SELECT ISNULL(last_name, '-') from customer
```

ket : ISNULL(last_name, '-') --> jika last_name berisi null maka replace jadi '-' jika tidak null maka tampilkan  last_name
padanannya :

```
select case when last_name  is not null then last_name  else '-'  end from customer 
```

## CASE WHEN

```
select case when last_name  is not null then last_name  else '-'  end from customer 
```

## Menampilkan SQL Server Execution Times, dll

```
set statistics IO on
SET STATISTICS TIME ON

select * from person_cluster where nama like '%LUKIK%'
```

