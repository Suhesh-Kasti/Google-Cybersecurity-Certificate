Let's start talking about the *syntax of joins*. Since we're working with two tables now, we need a way to tell SQL what table we're picking columns from. In SQL statements that contain two columns, SQL needs to know which column we're referring to. The way to resolve this is by writing the name of the table first, then a period, and then the name of a column. So, we would have employees followed by a period, followed by the column name. This is the employee_id column for the employees table. Similarly, this is the employee_id column for the machines table. 

Imagine that we want to get a deeper understanding of the employees accessing the machines in our company. By joining the employees and the machines tables, we can do this! We first need to identify the shared column that we'll use to connect the two tables. In this case, we'll use a *primary key* and one table to connect to another table where it's a *foreign key*. The primary key of the employees table is employee_id, which is a foreign key in the machines table. employee_id is a primary key in the employees table because it has a unique value for every row in the employees table, and no empty values. We don't have a guarantee that the employee_id column in the machines table follows the same criteria since it's a foreign key and not a primary key.

## Inner joins

The first type of join that you might perform is an inner join. INNER JOIN returns rows matching on a specified column that exists in more than one table.

![Venn diagram with two circles labeled "left table" and "right table". The intersection is highlighted.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/9y5ZKSySQTuS5RQ-MJLXrA_6b756cb30b9442c8ae576607a6ab3ff1_CS_R-080_Inner-joins.png?expiry=1690675200000&hmac=8KZQLSa53oKkfF_RYRXxRrJAsxW67gB7GrsN2h4IhDM)

It only returns the rows where there is a match, but like other types of joins, it returns all specified columns from all joined tables. For example, if the query joins two tables with SELECT *, all columns in both of the tables are returned.

**Note:** If a column exists in both of the tables, it is returned twice when SELECT * is used.

### The syntax of an inner join

To write a query using INNER JOIN, you can use the following syntax:

```SQL
SELECT *
FROM employees
INNER JOIN machines ON employees.device_id = machines.device_id;
```

You must specify the two tables to join by including the first or left table after FROM and the second or right table after INNER JOIN.

After the name of the right table, use the ON keyword and the = operator to indicate the column you are joining the tables on. It's important that you specify both the table and column names in this portion of the join by placing a period (.) between the table and the column.  

In addition to selecting all columns, you can select only certain columns.  For example, if you only want the join to return the username, operating_system and device_id columns, you can write this query:

```SQL
SELECT username, operating_system, employees.device_id
FROM  employees
INNER JOIN machines ON employees.device_id = machines.device_id;
```

**Note**: In the example query, username and operating_system only appear in one of the two tables, so they are written with just the column name. On the other hand, because device_id appears in both tables, it's necessary to indicate which one to return by specifying both the table and column name (employees.device_id).

## Outer joins

Outer joins expand what is returned from a join. Each type of outer join returns all rows from either one table or both tables.

### Left joins

When joining two tables, LEFT JOIN returns all the records of the first table, but only returns rows of the second table that match on a specified column. 

![Venn diagram with two circles labeled "left table" and "right table". The left circle and the intersection are highlighted.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/GsYCwSiOSMmymUqPUAQJ5w_5beed7e470c546fca088a83dfd9465f1_CS_R-080_Left-joins.png?expiry=1690675200000&hmac=5CpBEfm4AB7qpizl9ahou1Th_-7i_tsFAhRT8zSa0_o)

The syntax for using LEFT JOIN is demonstrated in the following query:

```SQL
SELECT *
FROM employees
LEFT JOIN machines ON employees.device_id = machines.device_id;
```

As with all joins, you should specify the first or left table as the table that comes after FROM and the second or right table as the table that comes after LEFT JOIN. In the example query, because employees is the left table, all of its records are returned. Only records that match on the device_id column are returned from the right table, machines. 

### Right joins

When joining two tables, RIGHT JOIN returns all of the records of the second table, but only returns rows from the first table that match on a specified column.

![Venn diagram with two circles labeled "left table" and "right table". The right circle and the intersection are highlighted.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/YHXRMOLiQheppUjthmM5yQ_cfb18a8315e34357bd1299f7eefafcf1_CS_R-080_Right-joins.png?expiry=1690675200000&hmac=l8zl1HYr_9lTLN14Gh_C9ZP8jqWzcp2LJf7vm7D9mkU)

The following query demonstrates the syntax for RIGHT JOIN:

```SQL
SELECT *
FROM employees
RIGHT JOIN machines ON employees.device_id = machines.device_id;
```

RIGHT JOIN has the same syntax as LEFT JOIN, with the only difference being the keyword RIGHT JOIN instructs SQL to produce different output. The query returns all records from machines, which is the second or right table. Only matching records are returned from employees, which is the first or left table.

**Note:**  You can use LEFT JOIN and RIGHT JOIN and return the exact same results if you use the tables in reverse order. The following RIGHT JOIN query returns the exact same result as the LEFT JOIN query demonstrated in the previous section:

```SQL
SELECT *
FROM machines
RIGHT JOIN employees ON employees.device_id = machines.device_id;
```

All that you have to do is switch the order of the tables that appear before and after the keyword used for the join, and you will have swapped the left and right tables.

### Full outer joins 

FULL OUTER JOIN returns all records from both tables. You can think of it as a way of completely merging two tables.

![Venn diagram with two circles labeled "left table" and "right table". Both circles are highlighted.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/oRzF__GaTqSGMmUqXKbSrQ_92db9841a00244c2aa214e60bb07f1f1_CS_R-080_FULL-OUTER-JOIN.png?expiry=1690675200000&hmac=HjqZJ6zNCoeeOny0QuRZAanYW2bs7R0PMqNq-m7dWNE)

You can review the syntax for using FULL OUTER JOIN in the following query:

```SQL
SELECT *
FROM employees
FULL OUTER JOIN machines ON employees.device_id = machines.device_id;
```
The results of a FULL OUTER JOIN query include all records from both tables. Similar to INNER JOIN, the order of tables does not change the results of the query.