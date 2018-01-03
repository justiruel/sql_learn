# STORE PROCEDURE
Di SQL Server, Store procedure disimpan di DATABASE > PROGRAMMABILITY > STORED PROCEDURES
## STATEMENT 1
```
Create Procedure Procedure-name 
(
Input parameters ,
Output Parameters (If required)
)
As
Begin
     Sql statement used in the stored procedure
End
```
## STATEMENT 2
```
Create  PROCEDURE GetName
AS
BEGIN
	print 'Halo dunia'
END
```

## SAMPLE CREATE PROCEDURE

```
Create  PROCEDURE GetName(
	@customerid INT     --Input parameter ,  Studentid of the student 
	--@studentname VARCHAR (200) OUT,    -- Output parameter to collect the student name
	--@StudentEmail VARCHAR (200)OUT     -- Output Parameter to collect the student email

)
AS
BEGIN
	IF (@customerid = 1)
	BEGIN
		print 'siji ga oleh'
	END
	ELSE
	BEGIN
		SELECT first_name +' '+last_name as Nama FROM customer WHERE id=@customerid 
	END
END
```
### CARA EKSEKUSI

```
Exec GetName 1
```

## ALTER PROCEDURE

```
Alter PROCEDURE GetName(
	@customerfirst VARCHAR(200),
	@customername VARCHAR(200) OUT -- Output parameter to collect the customer name
)
AS
BEGIN
	SELECT @customername = first_name +' '+last_name FROM customer WHERE first_name like '%'+@customerfirst+'%'
END
```

### CARA EKSEKUSI

```
Declare @customername as VARCHAR(200)
Exec GetName 'john', @customername output
select @customername as nama
```

## DROP SP

```
DROP PROCEDURE GetName;
DROP PROCEDURE IF EXISTS GetName;   ---> berlaku di sql server 2016 keatas
```


