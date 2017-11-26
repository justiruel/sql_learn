## Union
Perintah UNION digunakan untuk menggabungkan isi dari 2 (dua) tabel/query atau lebih. 
Perintah ini terdiri dari dua jenis, yaitu UNION dan UNION ALL. 

syarat field antara tabel/query 1 dengan yang lainnya harus sama.

### union
meng-ignore data yang isinya sama (seperti distinct), contoh :

```
select first_name,last_name from customer
union
select first_name,last_name from employee
```

pada query di atas john cena hanya tampil 1 row

### union all
semua data tampil walaupun isinya sama, contoh :

```
select first_name,last_name from customer
union all
select first_name,last_name from employee
```

pada query di atas john cena tampil semua

in case jika field table/query 1 dengan yg lainnya tidak sama maka bisa digantikan dengan null contoh :

```
select first_name,last_name,age from customer
union
select first_name,last_name,null from employee
```
