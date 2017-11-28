## JOIN

### In some databases JOIN is called INNER JOIN.

```
select * from customer c
JOIN employee e ON c.first_name = e.first_name        
```

### In some databases LEFT JOIN is called LEFT OUTER JOIN.

```
select * from customer c
LEFT JOIN employee e ON c.first_name = e.first_name        
```

### In some databases RIGHT JOIN is called RIGHT OUTER JOIN

```
select * from customer c
RIGHT JOIN employee e ON c.first_name = e.first_name        
```
### gabungan dari left dan right join, menampilkan data secara lengkap baik sisi kiri (customer) maupun sisi kanan (employee), dan data yang tidak ada akan terisi null 

```
select * from customer c
FULL JOIN employee e ON c.first_name = e.first_name        
```

### Query ini disebut Self JOIN, efeknya sama dengan inner join

```
select * from customer c,employee e 
where c.first_name = e.first_name
```
