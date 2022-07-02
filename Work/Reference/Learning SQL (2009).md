---
author: Beaulieu
genre: STEM
---
# Learning SQL (2009)
`SOURCE:` PDF
`TAGS:` #wip #book 

---
> [!Quick start]
> To access the [[MySQL]] database for this course, pass `sql/usr/local/mysql/bin/mysql -u root -p`, enter the standard old password ending in my initals, then pass `use bank;`. Now you're in the SQL database for the course!

# Preface
The book explains that [[SQL]] is broken into several categories. There are SQL *schema statements,* which are used to create [[database]] objects. There are also SQL *data statements* that create, manipulate, and retrieve [[data]] stored in a database (px). 

# 1. A little background
The author tells us that a database is just a set of related information (p1). 

Explaining [[relational databases]], the author says that each table in such a database includes unique information that identifies each row. This is known as the *primary key.* [[SQL primary keys identify rows]] (p5). 

In addition to these keys, he continues, *foreign keys* allow rows to be associated with rows in other tables. They're shared by multiple rows, and are therefore not unique. This is important since [[SQL organizes data in tables]] (p5). 

The author says that the relational model is clear on when to store redundant data, such as foreign keys. Only enough data to associate rows ought to be stored, such that the need to update information is minimized. For example, you shouldn't store a customer's name in multiple places because it may change. However, a `customer_id` should be stored in all rows that are associated with that customer. The process of refining a database to ensure each independent piece of information is in exactly one place is *normalization* (p6). [[Database normalization minimizes data redundancy]]. 

Interestingly, the author notes that SQL is *not* an acronym (p7). Wow, [[SQL is not an acronym]]! I didn't know that. 

The author explains that SQL is divided into seveal parts - SQL *schema statements,* *data statements,* and *transaction statements* which begin, end, and roll back transactions which will be covered in chapter 12 (p7). 

Describing [[schema]], the author says that all database elements that are created via schema statements are stored in the *data dictionary,* a special set of tables that represents [[metadata]] about the database (p8). 

The author reminds us that [[SQL is a declarative language]], and that the manner in which a statement is executed is left to the *optimizer* (p9). 

The author now turns to a general workflow when constructing a statement. We often determine the `FROM` clause, deciding which tables to pull data from. Then the `WHERE` clause determines the criteria and finally the `SELECT` clause decides what the specific information will look like (p11). 

# 2. Creating and populating a database
The book explains that character data can be stored as a fixed-length or variable-length string. Fixed length strings are right-padded with spaces and consume the same amount of bytes, while variable-length ones aren't padded and have variable storage size. We indicate fixed length using `char(20)` and variable length with `varchar(20)`. We have to indicate the maximum characters in either case. There is a maximum size in bytes, but we can get around that by using a `text` data type (p18).

In general, the author continues, we ought to use `char` when the length is going to be the same, such as state abbreviations or zip codes. When it isn't, use `varchar` (p19). 

The author explains that with longer text, such as whole documents, that might exceed the space limitations, use `mediumtext` or `longtext` data type (p21). 

Moving on to numeric data, the book says that we can use different data types for different purposes and size ranges. We can use `Tinyint`, `Smallint`, `Mediumint`, the general purpose `Int`, or even `Bigint`. If we want to use decimals, use `Float(p,s)` where `p` indicated precision (total number of places) and `s` determines scale (the number of allowable decimal places). For example, the float 3.1415 has a precision of 5 and a scale of 4 (p22). 

Turning to table creation, the book notes that when we define a table, we need to indicate which column or columns are the primary key. We do this by creating a *constraint* on the table. To create a primary key, create a primary constraint. Here's an example table with a primary constraint on the `person_id` column (p27). [[SQL constraints create keys]]. 

```sql
CREATE TABLE person
(person_id SMALLINT UNSIGNED,
 fname VARCHAR(20),
 lname VARCHAR(20),
 gender CHAR(1),
 CONSTAINT pk_person PRIMARY KEY (person_id)
 );
```

The book says that we can get a quick picture of a table by using `describe` or `desc` for short (p29). 

The author explains that primary keys can actually be combinations of two columns. For example, in the table above, we could have just as easily passed `CONSTRAINT pk_person_gender PRIMARY KEY (person_id, gender)`. By the way, we can also create foreign keys in a very similar way to this syntax (p30). 

Discussing how we can insert data into tables, the author says there are three main parts to an `insert` statement. We must specify the name of the table into which we're adding data, the names of the columns to be populated, and the values with which to populate them. Furthermore, we can automatically generate numeric primary keys with the following command (p31):

```sql
/* replace 'person' with any table name */
ALTER TABLE person MODIFY person_id SMALLINT UNSIGNED AUTO_INCREMENT;
```

The above command will begin to automatically increment `person_id` when new rows are added, so just pass `NULL` for the `person_id` when inserting a row. 

# 3. Query primer
Moving on to queries, the book explains that there are several clauses related to the `select` statement. We are often going to use one or more of the six available (p43). 

1. `select` - the mandatory one. Determines which columns to include in result set
2. `from` - identifies source tables and how they should be joined
3. `where` - filters unwanted data
4. `group by` - used to group rows by common column values
5. `having` - filters unwanted groups
6. `order by` - sorts final result

The author specifies that while the `SELECT` statement is the first clause we write, it's actually the last to be executed by the optimizer (p43). The `SELECT` clause determines which of all possible columns should be included in the final result set (p44).

The author reminds us that we can use the `distinct` clause right after `select` to get the unique results, but that this requires sorting behind the scenes, which can take a lot of time (p48). 

The `from` clause defines the tables used by a query, along with the means of linking the tables together (p48). 

A subquery is a query contained within another query. They can add useful complexity to more detailed queries (p49). For example:

```sql
select e.emp_id, e.fname, e.lname
from (
	select emp_id, fname, lname, start_date, title
	from employee ) e
);
```

A view is a query that gets stored in the data dictionary. It basically functions as a table that we can use for later, and there's no extra storage needed to keep views. The author calls views *virtual tables* (p50). [[SQL views function as virtual tables]]. 

The `where` clause is the mechanism to filter unwanted rows from the result set (p52). [[In SQL, WHERE filters rows, HAVING filters groups]]. 

We can use `group by` to *group* data by shared columns. For example, this query will return the number of employees per department (p54-55):

```sql
select d.name, count(e.emp_id) as num_employees
from department d inner join employee e
	on d.dept_id = e.dept_id
group by d.name;
```

If we didn't use `group by` above, the query wouldn't work. Whenever we aggregate, we have to group by something. 

We can use `order by` to sort the result set, either by raw column data or by an expression based on that data (p55). We can specify `asc` or `desc`, `asc` is default (p57). 

We can sort by expressions in this way (p58):

```sql
select cust_id, fed_id
from customer
order by right(fed_id, 3);
```

The query above sorts the result set by the right three digits in the `fed_id` column. We could just as easily use another expression. 

## Exercises
```sql
/* 3-1: Retrieve the employee ID, first name, and last name for all bank employees. Sort by last name and then by first name.*/

select emp_id, fname, lname
from employee
order by lname, fname;

/* 3-2: Retrieve the account ID, customer ID, and available balance for all accounts whose status equals 'ACTIVE' and whose available balance is greater than $2,500.*/

select account_id, cust_id, avail_balance
from account
where status = 'ACTIVE'
	and avail_balance > 2500;

/* 3-3: Write a query against the account table that returns the IDs of the employees who opened the accounts (use the account.open_emp_id column). 
Include a single row for each distinct employee. */

select distinct e.emp_id
from account a inner join employee e
	on a.open_emp_id = e.emp_id;

```

# 4. Filtering
The chapter begins with a note that all [[SQL data statements]] apart from `insert` contain an optional [[WHERE clause]] that will remove unwanted rows from the result set. A `where` clause is made up of one or more *conditions* separated by `and` or `or` operators (p63). 

The author recommends that when using more than three conditions we use parentheses to make it more clear. For example (p64):

```sql
select lname
from employee
where
	end date is null
	and (title = 'Teller' or start_date > '2007-01-01');
```

Moving on, a *condition* is made up of one or more *expressions* coupled with one or more operators. An expression could be a number, string, built-in function, subquery, etc (p66). 

There are various condition types, the first of which is an equality condition. In this condition, we check to see if a column is equal to an expression, for instance (p66):

```sql
select lname 
from employee
where
	title = 'Teller'
	fed_id = '111-11-1123'
	dept_id = (select dept_id from department where name = 'Loans');
```

In the above query, we're using a subquery to find the department id associated with 'Loans' and specifying that all results must have that department id. 

We can do the opposite with inequality conditions. For these, we can replace `=` with either `!=` or `<>` (p67). 

If we want to specify a range, we can use the `between` operator. Note that this operator is *inclusive* (p69-70). 

We can even use ranges for strings, for instance we can find rows where `fed_id` is between `000-00-0001` and `999-99-9999`. We just have to know the way that characters are ordered in our character set, known as the *collation* (p70-71).

When checking for membership in a set, we can use the `in` operator along with a comma-separated group in parentheses, or we can use a subquery (p71-72).  

We can use *wildcards* to find partial string matches. This is like a built-in simplified set of [[regex]] (p73-74). 

| character | meaning                  |
| --------- | ------------------------ |
| `_`       | exactly one character    |
| %         | any number of characters | 

When using these, we have to specify `fed_id LIKE __1-_2_-1203` rather than using `=`. 

Of course, we can use regex, by passing `fed_id REGEX` and then whatever regex we want to use (p75). 

The author begins a discussion of `NULL` by saying that it can represent a few different things. It could mean that the field is not applicable, not yet known, or undefined. This makes it hard to know exactly what a NULL is saying unless you're familiar with the data. When working with NULLs, we should remember that an expression can *be* null, but cannot *equal* null. Two nulls are not equal to each other (p76). When working with a database, we should find out which columns can be null so that rows don't fall through the cracks. This is important, because if we pass a query like so:

```sql
select name
from employees
where
	position != 'clerk';
```

... this will actually include those whose positions are `NULL`, which we might not want (p78). 

## Exercises
```sql
/* 4-3: Construct a query that retrieves all accounts opened in 2002 */

select account_id, txn_date
from transaction
where year(txn_date) = '2002';

/* 4-4: Construct a query that finds all nonbusiness customers whose last name contains an a in the second position and an e anywhere after the a. */

select * 
from individual
where lname like '_a%e%';
```

# 5. Querying multiple tables
Beginning the section on joins, the author explains that the *inner join* is the most common type, and is the default join type when we don't specify anything (p85). This join only includes rows that have a common match for whatever is specified as the joining column (p84). 

The book explains that there are cases where we may want to join three or more tables together. In these cases, we have to specify two join types in the `from` clause, and two `on` sub-clauses to specify joining key (p88).

The book explains that theo order we join tables doesn't matter, since the optimizer decides how to do it in the best way. The server picks one of the tables and uses it as the *driving table* to accomplish the join in the most efficient way possible. There is a method for specifying the order, but we don't really have to (p90).

If we're joining multiple tables, the author says, we might have to join the same table more than once. In the sample database, there are foreign keys into the `branch` table from both the `account` table and the `employee` table. If we want to include both branches in the result, we have to use the `branch` table twice (p92):

```sql
select a.account_id, e.emp_id, b1.name open_branch, b2.name emp_branch
from account a 
	inner join branch b1
		on a.open_branch_id = b1.branch_id
	inner join employee e
		on a.open_emp_id = e.emp_id
	inner join branch b2
		on e.assigned_branch_id = b2.branch_id
where a.product_cd = 'CHK';
```

The book explains that we can go further and join a table to itself if we want. For example, in the sample database there's an employee table that has `emp_id` and `superior_emp_id` to note the `emp_id` of a worker's boss. If we want a list of workers and their bosses, we can join the table to itself (p93):

```sql
select e.fname, mgr.fname
from employee e inner join employee mgr
	on e.superior_emp_id = mgr.emp_id;
```

The book turns to a discussion of equi-joins and non-equi joins. Normally, to specify the `on` subclause, we just say one column is equal to another. That's an equi-join, but we don't have to do it that way if we want to join tables that have no direct foreign key relationship. For example, if we want to attach a range of values to a singular one from another table, we can do so (p94):

```sql
select e.emp_id, e.fname, e.start_date
from employee e inner join product p
	on e.start_date >= p.date_offered
		and e.start_date <= p.date_retired
where p.name = 'no-fee checking';
```

The query above gets the employee id, employee name, and employee start date for all employees that started after the date that the no-fee checking product was offered, but before it was retired. 

## Exercises
```sql
/* 5-2: Write a query that returns the account ID for each nonbusiness customer (customer.cust_type_cd = 'I') with the customer’s federal ID (customer.fed_id) and the name of the product on which the account is based (product.name). */

select a.account_id, c.fed_id, p.name
from account a 
inner join customer c
	on a.cust_id = c.cust_id
inner join product p
	on a.product_cd = p.product_cd
where c.cust_type_cd = 'I';

/* 5-3: Construct a query that finds all employees whose supervisor is assigned to a different department. Retrieve the employees’ ID, first name, and last name. */

select e1.emp_id, e1.fname, e1.lname
from employee e1
inner join employee e2
	on e1.superior_emp_id = e2.emp_id
where e2.dept_id != e1.dept_id;
```

# 6. Working with sets
Turning to a description of set theory, the author says that two guidelines apply when performing set operations on two datasets: both datasets must have the same number of columns, and the data types across the columns must be identical (p102). 

The `union` operator allows us to combine all the rows of multiple datasets. For example (p103):

```sql
select cust_id, fname
	from individual_customers
union
select cust_id, business_name
	from business_customers;
```

This query would combine all the rows from both of these tables, and remove *most* duplicates. If we want to keep duplicates, we can pass `union all` instead of `union`. 

We can use the `intersect` operator to return rows found in both tables, but this isn't supported in all versions of [[MySQL]] (p103). The same issue applies to the `except` operator, which returns all rows of one database *not* found in another (p107). 

When we use `order by` in these statements, we need to use the column names found in the *first* table (p108). 

Unlike queries in general, we do have to think about the order in which we specify set operations. Compound queries are evaluated from top to bottom (p111). 

## Exercises
```sql
/* 6-1: If set A = {L M N O P} and set B = {P Q R S T}, what sets are generated by the following operations? 
• A union B --> {L M N O P Q R S T}
• A union all B --> {L M N O P P Q R S T}
• A intersect B --> {P}
• A except B --> {L M N O}
*/

/*6-2: Write a compound query that finds the first and last names of all individual customers along with the first and last names of all employees.*/

select fname, lname
	from individual
union
select fname, lname
	from employee;

/*6-3: Sort the results from Exercise 6-2 by the lname column.*/ 

select fname, lname
	from individual
union
select fname, lname
	from employee
order by lname;
```

# 7. Data generation, conversion, and manipulation
The book now dives into an explanation of the various built-in functions that can manipulate data within SQL, starting with string functions:

- `quote()` <-- automatically add escape characters to string (p116)
- `length()` <-- return length of string (p119)
- `position('substring' IN field)` <-- find position of substring in string (p119)
- `locate('substring', field, n)`  <-- similar to position(), specifies n start point (p120)
- `strcmp('string1', 'string2')`  <-- returns -1 if string1 comes before string2, 0 if identical, 1 if first string after second string (p120)
- `like()` and `regexp()` <-- return 1 if true, 0 if false (p122)
- `concat()` <-- add additional text to field (p123)
- `insert('original string', x, y, 'new string')` <-- inserts 'new string' at position x, replacing the next y characters with the new string. Set y to zero to do a pure insert with no replacement (p124)

There are a variety of single-argument mathematical functions that I won't enumerate. These are things like `Sqrt(x)`, `Cos(x)`, etc (p126). 

Now we move on to numeric functions:

- `modulo(x,y)` <-- calculates the remainder of $x/y$ (p127)
- `pow(x,y)` <-- calculates $x^y$ (p127)
- `sign(x)` <-- returns 1 if x is positive, 0 if x is zero, and -1 if x is negative (p130)
- `abs(x)` <-- returns $|x|$ (p130)

We can use four functions when specifying precision of floating-point numbers. We can round up with `ceil()`, round down with `floor()`, round relative to the midpoint of the decimal using `round()`, or remove unwanted digits without rounding using `truncate(x, n)`. With that last one, we can specify to keep `n` decimals (p128-129).

Moving along to datetime operations, we can return the current UTC timestamp with `utc_timestamp()`. This is a common unifying timestamp for SQL (p131).

There are various datetime components that we sometimes have to specify (p134):

| Component | Definition    |
| --------- | ------------- |
| YYYY      | year          |
| MM        | month         |
| DD        | day           |
| HH        | hour          |
| HHH       | hours elapsed |
| Mi        | minute        |
| SS        | second        | 

If we need to change the data type, we can perform `cast(x AS new_type)`, but SQL also has built-in `str_to_date()` function (p135). 

If we need the last day of a month, use `last_day()` (p138). If we need the name of the day, use `dayname()`, and if we need the difference between dates `x` and `y`, use `datediff(x,y)` (p139-140). 

## Exercises
```sql
/*7-1: Write a query that returns the 17th through 25th characters of the string 'Please find the substring in this string'.*/

select substring('Please find the substring in this string', 17, 9);

/*7-2: Write a query that returns the absolute value and sign (−1, 0, or 1) of the number −25.76823. Also return the number rounded to the nearest hundredth.*/

select abs(-25.76823), sign(-25.76823), round(-25.76823, 3);

/*7-3: Write a query to return just the month portion of the current date.*/

select month(utc_timestamp());
```

# 8. Grouping and aggregates
...

# 9. Subqueries
...

# 10. Joins revisited
...

# 11. Conditional logic
...

# 12. Transactions
...

# 13. Indexes and constraints
...

# 14. Views
...

# 15. Metadata
...