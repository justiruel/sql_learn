## LIMIT AND OFFSET
Di sql server tidak mengenal fungsi limit offset seperti di mysql
contoh mysql :

```
select * from customer order by first_name asc limit 2,5
```
ket :  2 -> jumlah baris yang tidak ditampilkan dihitung dari baris pertama, 5 -> jumlah baris yang akan ditampilkan

Alternatif di sql server adalah dengan memanfaatkan id auto_increment atau bisa juga memanfaatkan method ROW_NUMBER()

### fungsi dari ROW_NUMBER adalah menampilkan nomor urut row, contoh
```
select *, ROW_NUMBER() over(order by first_name asc) as row_number from customer
```

### contoh offset limit dengan ROW_NUMBER()

```
select top 5 * from (
	select *, ROW_NUMBER() over (order by first_name asc) as row_number from customer 
) as mytable where row_number > 2 
```

### contoh dengan id auto_increment

```
select top 5 * from customer where id > 2 
```
ket : kelemahan memanfaatkan id 
- id harus urut jika ada sebagian row yang dihapus sehinggal membuat id loncat-loncat maka cara ini tidak bisa dipakai 
- tidak bisa di order by selain id karena urutan id akan kacau
