## Trigger
Di SQL Server, Trigger disimpan di DATABASE > TABLES > TABLE_NAME > Triggers

ref : https://www.codeproject.com/Articles/25600/Triggers-SQL-Server
isi dari tutorial :
- AFTER INSERT Trigger
- AFTER UPDATE Trigger
- AFTER DELETE Trigger
- INSTEAD OF INSERT Trigger
- INSTEAD OF UPDATE Trigger
- INSTEAD OF DELETE Trigger

```
AFTER INSERT/UPDATE/DELETE adalah untuk memberi perintah apa yang harus dilakukan setelah insert/update/delete
```

```
INSTEAD OF INSERT/UPDATE/DELETE adalah sebagai intenceptor, yaitu misalkan terjadi perintah delete (delete from Employee_Test where Emp_ID=4)
dengan memanfaatkan INSTEAD OF sebelum proses delete terjadi kita bisa memasukkan sebuah logika <b>if Emp_ID == 4  then ROLLBACK else COMMIT</b>
```

### Contoh 

```
CREATE TRIGGER trgAfterInsert ON [dbo].[customer] 
FOR INSERT
AS
	declare @log varchar(MAX);
	declare @dataKeterangan varchar(MAX);
	
	select @log = first_name+' '+last_name from inserted i;	
	
	set @dataKeterangan='Inserted Record -- After Insert Trigger.';

	insert into [log] values(@log,@dataKeterangan);

	PRINT 'AFTER INSERT trigger fired.'
GO

```

cara eksekusi :
```
insert into customer values ('andi','malarangeng','50',7);
```

ket. pada trigger, <b>inserted</b> adalah mengacu pada data yang di insert
