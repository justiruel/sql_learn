# TRANSACTION
Transaction digunakan untuk memastikan semua query yang akan dieksekusi terhindar dari error, apabila ada salah satu query yang error maka semua proses query sebelumnya misal (insert, update, delete) akan dibatalkan/rollback

Contoh Table :

```
CREATE TABLE T
(
    DATAKU [nvarchar](100) NOT NULL UNIQUE,
);
```

CARA 1 :

```
BEGIN TRANSACTION [Tran1]

BEGIN TRY

  INSERT INTO T VALUES ('A');
  INSERT INTO T VALUES ('B');
  INSERT INTO T VALUES ('B');
  INSERT INTO T VALUES ('C');

COMMIT TRANSACTION [Tran1]

END TRY
BEGIN CATCH
  ROLLBACK TRANSACTION [Tran1]
  --PRINT ERROR_MESSAGE()
  RAISERROR('DATA HARUS UNIK!',16,1);
END CATCH  

```

CARA 2 :

```
SET XACT_ABORT ON -- Turns on rollback if T-SQL statement raises a run-time error.
--SELECT * FROM T; -- Check before.
BEGIN TRAN
    INSERT INTO T VALUES ('A');
    INSERT INTO T VALUES ('B');
    INSERT INTO T VALUES ('B');
    INSERT INTO T VALUES ('C');
COMMIT TRAN
--SELECT * FROM T; -- Check after.
--DELETE T;
```

ket. 'B' di insert 2 kali sedangkan saat create table field di definisikan sebagai unique field sehingga jika 'B' di insert 2 kali maka akan terjadi error, dengan bantuan transaction maka tidak ada satupun data yang terinsert (semua di rollback), dengan demikian tidak ada data yang tercecer
