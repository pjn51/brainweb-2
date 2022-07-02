---

---
# SQL views function as virtual tables. 
In [[SQL]], we can store queries to the data dictionary. This means that we can store them for later queries. For example, we can create a view like so:

```sql
mysql>create view employee_vw as
	->select emp_id, fname, lname,
	->year(start_date) as start_year
	->from employee;
	
Query OK, 0 rows affected (0.10 sec)
```

Then we can query this view:

```sql
mysql>select emp_id, start_year
	->from employee_vw
	->limit 1;

+--------+------------+ 
| emp_id | start_year |
+--------+------------+
|      1 |       2005 |
+--------+------------+
```

---
#idea/compsci/sql 