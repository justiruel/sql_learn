## ORDER BY 
Order by dapat lebih dari 1 field<br/>
Contoh :

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
    <td>7</td><td>joko</td><td>widodo</td><td>50</td><td>2</td>
  </tr>  
  <tr>
    <td>8</td><td>jajang</td><td>nurjaman</td><td>50</td><td>2</td>
  </tr>  
  <tr>
    <td>9</td><td>andi</td><td>NULL</td><td>40</td><td>1</td>
  </tr>  
  <tr>
    <td>10</td><td>idrus</td><td>arham</td><td>30</td><td>1</td>
  </tr> 
</table>  

```
select * from customer order by first_name,last_name asc
```
Ket : Data akan di urut berdasarkan first_name secara ascending, jika ada beberapa record yang isi first_name-nya sama, maka diurut berdasarkan last_name
pada contoh di atas ada 2 record yang memiliki value 'idrus' maka record yang didahulukan adalah 'idrus arham' lalu 'idrus ramli'.
