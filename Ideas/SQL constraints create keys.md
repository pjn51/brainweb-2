---

---
# SQL constraints create keys. 
Since [[SQL primary keys identify rows]], we have to create primary keys when creating tables. We do this by creating a *constraint* on a specific column. Here's an example table with a primary key constraint passed on `person_id`:

```sql
CREATE TABLE person
(person_id SMALLINT UNSIGNED,
 name VARCHAR(20),
 gender CHAR(1),
 CONSTAINT pk_person PRIMARY KEY (person_id)
 );
```

---
#idea/compsci/sql 