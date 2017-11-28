## QUERY DASAR

```
insert into tableName (field1,field2) values ('field1','field2')
select * from tableName
update tableName set field2 = 'abc' where field1 = 'xyz'
delete from tableName where field1 = 'xyz'
```

## SPECIAL INSERT

```
insert into tableName (field1,field2) select fieldA,fieldB from tableX
```
ket. nama field antara insert statement dan select statement tidak harus sama, yang penting tipe data sesuai dan jumlah field yang akan di insert dan yang di select sama

## UPDATE JOIN

```
update u
set u.assid = s.assid
from ud u
    inner join sale s on
        u.id = s.udid
```


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


## Convert Date

```
SELECT CONVERT(varchar, GETDATE(), 101);
```

ref : https://www.w3schools.com/sql/func_sqlserver_convert.asp


## akses lengkap table

```
select * from [database].[dbo].[table_name]
```
ket. kurung balok/[]  bisa digunakan untuk nama field yang ada spasi-nya misal :

```
select * from log where [data keterangan] like '%halo%'
```
