## HAVING

Jika ingin menampilkan data dengan kondisi tertentu kita bisa menggunakan 'WHERE' namun
jika ingin menampilkan data dari fungsi agregat (sum, count,avg dll.) atau hasil grouping lalu kita ingin memberikan kondisi tertentu kita tidak bisa menggunakan 'WHERE'
maka sebagai gantinya kita menggunakan 'HAVING'
dengan kata lain 'HAVING' digunakan sebagai pengganti 'WHERE' di fungsi agregat / hasil grouping

contoh : 
id	first_name	last_name	age	level
1	  john		    cena		  12	1
2	  idrus		    ramli		  34	1
3	  firanda		  adireja		40	1
4	  doni		    kusuma		45	1
5	  celine 		  dion		  49	2
6	  marzuki		  darusman	60	2
7	  joko		    widodo		50	2
8	  jajang		  nurjaman	50	2
9	  andi		    NULL		  40	1
10	idrus		    arham		  30	1

```
select COUNT(age) as jumlah, level from customer group by level having SUM(age) = 209
```

Penjelasan : 
1. select jumlah age secara keseluruhan grup berdasarkan level :
hasil :

jumlah	level
6	    	1
4		    2

2. hasil gruping diatas di-query lagi menggunakan perintah having (having digunakan untuk pengganti where saat kita menggunakan gruping/agregate(sum, avg, dll)) :
  -  semua nilai age pada level 1 di sum apakah = 209
  -  semua nilai age pada level 2 di sum apakah = 209
  -  yang bersesuaian di tampilkan, hasilnya :
  
jumlah	level
4		    2
