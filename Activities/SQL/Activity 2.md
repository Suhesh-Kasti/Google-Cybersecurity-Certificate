## Task 1. List all organization machines

In this task, you need to get a list of all organization machines and their operating systems. The data is contained in the `machines` table. You’ll need to use the `SELECT` keyword to return specific columns.

- Run a SQL query to retrieve only the `device_id` and `operating_system` columns from the `machines` table.

The command to complete this step:

```SQL
SELECT device_id, operating_system 
FROM machines;
```

The output lists only the selected columns from all the rows in the `machines` table:

+--------------+------------------+
| device_id    | operating_system |
+--------------+------------------+
| a184b775c707 | OS 1             |
| a192b174c940 | OS 2             |
| a305b818c708 | OS 3             |
| a317b635c465 | OS 1             |
| a320b137c219 | OS 2             |
| a398b471c573 | OS 3             |
|...                              |
+--------------+------------------+
200 rows in set (0.028 sec)

How many rows were returned from the machines table? (You can view the number of rows at the bottom of the output.)
**Answer**: The `machines` table returned 200 rows.

## Task 2. Retrieve a list of the machines with OS 2

In this task, you need to obtain a list of all machines with the `'OS 2'` operating system because these machines need an update. To get this information, you’ll run your first SQL query with a filter.

- Select all the records from the `machines` table with a value of `'OS 2'` in the `operating_system` column. Replace the value `X` with the correct string:

SELECT device_id, operating_system
FROM machines 
WHERE operating_system = 'X';

The command to complete this step:

```SQL
SELECT device_id, operating_system 
FROM machines 
WHERE operating_system = 'OS 2';
```

_**Note:** The `WHERE` clause allows you to filter the results returned by a query by returning only the records that satisfy the condition._

The output displays the selected columns of the `machines` table, filtered by the operating system:

+--------------+------------------+
| device_id    | operating_system |
+--------------+------------------+
| a192b174c940 | OS 2             |
| a320b137c219 | OS 2             |
| a821b452c176 | OS 2             |
| b157c491d493 | OS 2             |
| b264c773d977 | OS 2             |
|...                              |
+--------------+------------------+
80 rows in set (0.264 sec)
**Answer**: There are 80 machines in the database that use the OS 2 operating system.

## Task 3. List employees in specific departments

In this task, you need to retrieve a list of all the employees in the Finance and Sales departments to obtain their office numbers. A notice about handling confidential financial information will be posted to these offices.

1. Filter the rows returned from `department` column in the `employees` table to include only employees from the `'Finance'` department. Replace `X` with the appropriate column name and `Y` with the appropriate value to complete the filter:

SELECT * 
FROM employees 
WHERE X = 'Y';

The correct query to solve this step:

```SQL
SELECT * 
FROM employees 
WHERE department = 'Finance';
```

The output displays the contents of the `employees` table, including only employees in the Finance department.

What is the employee_id of the first row returned?
**Answer**: The `employee_id` of the first row returned is 1003.

2. Modify the previous query so that it returns employees who are in the `'Sales'` department.

The correct query to solve this step:

```SQL
SELECT * 
FROM employees 
WHERE department = 'Sales';
```


The output will display the contents of the `employees` table, including only employees in the Sales department.

How many employees work in the Sales department?
**Answer**: There are 33 employees who work in the Sales department.

## Task 4. Identify employee machines

Your team recently discovered that there are issues with machines in the South building. In this task, you need to obtain certain employee and computer information.

A machine in `'South-109'` has an issue. You need to determine which employee uses that computer so you can send them an alert.

1. Write a query to identify which employee uses the office in `'South-109'`. (The data must be returned from the `office` column in the `employees` table.)

The correct query to solve this step:

```SQL
SELECT * 
FROM employees 
WHERE office = 'South-109';
```
Which of the following employees uses the computer with the issue?
**Answer**: The user ID of the employee with the computer issue is jlansky.

Next, your team has determined that there is an issue with all the machines in the South building. Offices in the organization are named with the building name, a hyphen, and the office number in that building (for example, `'South-109'`).

2. Modify the query you used in the previous step so that it returns information on all the employees in the `'South'` building. Use the `LIKE` operator with `%` in this query.

The correct query to solve this step:

```SQL
SELECT * 
FROM employees 
WHERE office LIKE 'South%';
```

_**Note:** The `LIKE` keyword in SQL performs simple string matches. The matching pattern may include the wildcard `%` to represent a string of any length. This wildcard may be placed both before and after the targeted substring._

Which department does the first employee listed in the South building belong to?
**Answer**: The first employee on the list returned works in the Finance department.