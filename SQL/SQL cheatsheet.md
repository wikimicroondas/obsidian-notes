# where
## List elements
```sql
where author in('Theodore Dreiser', 'Ayn Rand', 'Harper Lee', 'Mark Twain')
```

## Comparisons

| operator | description                     |
| -------- | ------------------------------- |
| !<, !>   | not less than, not greater than |
| <>, !=   | not equal                       |
# insert into
```sql
INSERT INTO customers (name, surname, zip_code, city) 
VALUES ('Bobby', 'Ray', 60601, 'Chicago'),
	   ('Steve', 'Palmer', 33107, 'Miami'); --- ...N
```
# update
```sql
UPDATE employees 
SET department_id = 14, 
    salary = salary + 10000;
```
# delete from
```sql
DELETE FROM books 
WHERE quantity = 0;
```