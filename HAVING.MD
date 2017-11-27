## HAVING

Jika ingin menampilkan data dengan kondisi tertentu kita bisa menggunakan 'WHERE' namun
jika ingin menampilkan data dari fungsi agregat (sum, count,avg dll.) atau hasil grouping lalu kita ingin memberikan kondisi tertentu kita tidak bisa menggunakan 'WHERE'
maka sebagai gantinya kita menggunakan 'HAVING'
dengan kata lain 'HAVING' digunakan sebagai pengganti 'WHERE' di fungsi agregat / hasil grouping

contoh : 
<table>
  <tr>
    <th>id</th><th>first_name</th><th>last_name</th><th>age</th><th>level</th>
  </tr>
  <tr>
    <td>1</td><td>john</td><td>cena</td><td>12</td><td>1</td>
  </tr>
  <tr>
    <td>2</td><td>idrus</td><td>ramli</td><td>34</td><td>1</td>
  </tr>
  <tr>
    <td>3</td><td>firanda</td><td>adireja</td><td>40</td><td>1</td>
  </tr>
  <tr>
    <td>4</td><td>doni</td><td>kusuma</td><td>45</td><td>1</td>
  </tr>
  <tr>
    <td>5</td><td>celine</td><td>dion</td><td>49</td><td>2</td>
  </tr>
  <tr>
    <td>6</td><td>marzuki</td><td>darusman</td><td>60</td><td>2</td>
  </tr>  
  <tr>
    <td>7</td><td>joko</td><td>widodo</td><td></td>50<td>2</td>
  </tr>  
  <tr>
    <td>8</td><td>jajang</td><td>nurjaman</td>50<td></td><td>2</td>
  </tr>  
  <tr>
    <td>9</td><td>andi</td><td>NULL</td><td>40</td><td>1</td>
  </tr>  
  <tr>
    <td>10</td><td>idrus</td><td>arham</td><td>30</td><td>1</td>
  </tr> 
</table>  


```
select COUNT(age) as jumlah, level from customer group by level having SUM(age) = 209
```

Penjelasan : 
1. select jumlah age secara keseluruhan grup berdasarkan level :
hasil :

<table>
  <tr>
    <th>jumlah</th><th>level</th>
  </tr>
  <tr>
    <td>6</td><td>1</td>
    <td>4</td><td>2</td>
  </tr>
</table>

2. hasil gruping diatas di-query lagi menggunakan perintah having (having digunakan untuk pengganti where saat kita menggunakan gruping/agregate(sum, avg, dll)) :
  -  semua nilai age pada level 1 di sum apakah = 209
  -  semua nilai age pada level 2 di sum apakah = 209
  -  yang bersesuaian di tampilkan, hasilnya :
  
<table>
  <tr>
    <th>jumlah</th><th>level</th>
  </tr>
  <tr>
    <td>4</td><td>2</td>
  </tr>
</table>
