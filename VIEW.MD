## Contoh View
```
CREATE VIEW view_customer AS
select * from customer where age < 40
```

## Cara Pemanggilan
```
select * from view_customer where first_name = 'idrus'
```
## Drop View

```
DROP VIEW view_customer
```

