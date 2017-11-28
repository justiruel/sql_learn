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

## CONTOH TRIGGER

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


## CONTOH INSTEAD OF DELETE TRIGGER

```
CREATE TRIGGER trgInsteadOfDelete ON [dbo].[customer] 
INSTEAD OF DELETE
AS
	declare @emp_id varchar(MAX);
	declare @emp_age varchar(MAX);
	declare @emp_firstname varchar(MAX);
	declare @emp_lastname varchar(MAX);
	
	select @emp_id= d.id from deleted d;
	select @emp_age=d.age from deleted d;
	select @emp_firstname=d.first_name from deleted d;
	select @emp_lastname=d.last_name from deleted d;

	BEGIN
		if(@emp_age<70)
		begin
			RAISERROR('Usia minimum yang bisa dihapus adalah 70',16,1);
			--ROLLBACK;
		end
		else
		begin
			delete from customer where id=@emp_id;
			--COMMIT;
			insert into log values (@emp_firstname+' '+@emp_lastname,'Record Deleted -- Instead Of Delete Trigger.');
			PRINT 'Record Deleted -- Instead Of Delete Trigger.'
		end
	END
GO
```

Cara eksekusi :

```
delete from customer where id = 18
```

ket. 
1. delete from customer where id = 18
2. deleted = select * from customer where id = 18
3. masukkan id,age,first_name dan last_name kedalam variable
4. kondisi jika age < 70 maka munculkan pesan error dan perintah hapus tidak dijalankan
5. jika sebaliknya maka lakukan perintah delete
6. insert ke table log
