## Task 1. Match employees to their machines

First, you must identify which employees are using which machines. The data is located in the `machines` and `employees` tables.

You must use a SQL inner join to return the records you need based on a connecting column. In the scenario, both tables include the `device_id` column, which you’ll use to perform the join.

1. Run the following query to retrieve all records from the `machines` table:

```SQL
SELECT * 
FROM machines;
```

You’ll note that this query is not sufficient to perform the join and retrieve the information you need.

2. Complete the query to perform an inner join between the `machines` and `employees` tables on the `device_id` column. Replace `X` and `Y` with this column name:

```SQL
SELECT * 
FROM machines 
INNER JOIN employees ON machines.X = employees.Y;
```

_**Note:** Placing the `employees` table after `INNER JOIN` makes it the right table._

To complete a join you need to link the joined tables on a common column. In the case of the `employees` and `machines` tables, the `device_id` column is common.

The correct query to solve this step:

```SQL
SELECT * 
FROM machines 
INNER JOIN employees ON machines.device_id = employees.device_id;
```

_**Note:** If the output of the query is too wide for your shell, press the **Open Linux Console** button described in the Lab features section to open a full-screen view of the Bash shell, where you can re-enter the query._

How many rows did the inner join return?
**Answer**: The inner join query returned 185 rows.


## Task 2. Return more data

You now must return the information on all machines and the employees who have machines. Next, you must do the reverse and retrieve the information of all employees and any machines that are assigned to them.

To achieve this, you’ll complete a left join and a right join on the `employees` and `machines` tables. The results will include all records from one or the other table. You must link these tables using the common `device_id` column.

1. Run the following SQL query to connect the `machines` and `employees` tables through a left join. You must replace the keyword `X` in the query:

```SQL
SELECT * 
FROM machines 
X JOIN employees ON machines.device_id = employees.device_id;
```

The correct query to solve this step:

```SQL
SELECT * 
FROM machines 
LEFT JOIN employees ON machines.device_id = employees.device_id;
```

_**Note:** In a left join, all records from the table referenced after `FROM` and before `LEFT JOIN` are included in the result. In this case, all records from the `machines` table are included, regardless of whether they are assigned to an employee or not._

What is the value in the username column for the last record returned?
**Answer**: The last username returned is NULL.

2. Run the following SQL query to connect the `machines` and `employees` tables through a right join. You must replace the keyword `X` in the query to solve the problem:

```SQL
SELECT * 
FROM machines
X JOIN employees ON machines.device_id = employees.device_id;
```

_**Note:** In a right join, all records from the table referenced after `RIGHT JOIN` are included in the result. In this case, all records from the `employees` table are included, regardless of whether they have a machine or not._

The correct query to solve this step:

```SQL
SELECT * 
FROM machines 
RIGHT JOIN employees ON machines.device_id = employees.device_id;
```

What is the value in the username column for the last record returned?
**Answer**: The value in the username column for the last record returned is areyes.

## Task 3. Retrieve login attempt data

To continue investigating the security incident, you must retrieve the information on all employees who have made login attempts. To achieve this, you’ll perform an inner join on the `employees` and `log_in_attempts` tables, linking them on the common `username` column.

- Run the following SQL query to perform an inner join on the `employees` and `log_in_attempts` tables. Replace `X` with the name of the right table. Then replace `Y` and `Z` with the name of the column that connects the two tables:

```SQL
SELECT * 
FROM employees 
INNER JOIN X ON Y = Z;
```
_**Note:** You must specify the table name with the column name (table.column) when joining the tables._

The correct query to solve this step:

```SQL
SELECT * 
FROM employees 
INNER JOIN log_in_attempts ON employees.username = log_in_attempts.username;
```

How many records are returned by this inner join?
**Answer**: There are 200 records returned by the inner join.