The two SQL keywords we need for basic SQL queries are ***SELECT*** and ***FROM***. **SELECT** indicates which columns to return. **FROM** indicates which table to query. The use of these keywords in SQL is very similar to how we would use these words in everyday language. For example, we can ask a friend to select apples and bananas from the big box when going out to buy fruit. This is already very similar to SQL.

Let's use SELECT and FROM in SQL to return the information we need on employees and the computers they use. We start off by typing in the SQL statement. After FROM, we've identified that the information will be pulled from the employees table. And after SELECT, employee_id and device_id indicate the two columns we want to return from this table. Notice how a comma separates the two columns that we want to return.

It's also worth mentioning a couple of key aspects related to the syntax of SQL here. **Syntax** refers to the rules that determine what is correctly structured in a computing language. In SQL, *keywords are not case-sensitive*, so you could also write select and from in lowercase, but we're placing them in capital letters because it makes the query easier to understand. Another aspect of this syntax is that *semicolons are placed at the end* of the statement.

## Basic SQL query

There are two essential keywords in any SQL query: SELECT and FROM. You will use these keywords every time you want to query a SQL database. Using them together helps SQL identify what data you need from a database and the table you are returning it from.

```SQL
SELECT employee_id, device_id

FROM employees;
```

In readings and quizzes, this course uses a sample database called the Chinook database to run queries. The Chinook database includes data that might be created at a digital media company. A security analyst employed by this company might need to query this data.  For example, the database contains eleven tables, including an employees table, a customers table, and an invoices table. These tables include data such as names and addresses.  

As an example, you can run this query to return data from the customers table of the Chinook database:

```SQL
SELECT *

FROM customers;
```



### **SELECT**

The SELECT keyword indicates which columns to return. For example, you can return the customerid column from the Chinook database with

```SQL
SELECT customerid
```

You can also select multiple columns by separating them with a comma. For example, if you want to return both the customerid and city columns, you should write SELECT customerid, city.

If you want to return all columns in a table, you can follow the SELECT keyword with an asterisk (\*). The first line in the query will be SELECT .

**Note:** Although the tables you're querying in this course are relatively small, using SELECT * may not be advisable when working with large databases and tables; in those cases, the final output may be difficult to understand and might be slow to run. 

### **FROM**

The SELECT keyword always comes with the FROM keyword. FROM indicates which table to query. To use the FROM keyword, you should write it after the SELECT keyword, often on a new line, and follow it with the name of the table you’re querying. If you want to return all columns from the customers table, you can write:

```SQL
SELECT *

FROM customers;
```

When you want to end the query here, you put a semicolon (;) at the end to tell SQL that this is the entire query.

**Note:** Line breaks are not necessary in SQL queries, but are often used to make the query easier to understand. If you prefer, you can also write the previous query on one line as

SELECT * FROM customers;

## ORDER BY

Database tables are often very complicated, and this is where other SQL keywords come in handy. ORDER BY is an important keyword for organizing the data you extract from a table.

ORDER BY sequences the records returned by a query based on a specified column or columns. This can be in either ascending or descending order.

### **Sorting in ascending order**

To use the ORDER BY keyword, write it at the end of the query and specify a column to base the sort on. In this example, SQL will return the customerid, city, and country columns from the customers table, and the records will be sequenced by the city column:
```SQL
SELECT customerid, city, country

FROM customers

ORDER BY country;

```

The ORDER BY keyword sorts the records based on the column specified after this keyword. By default, as shown in this example, the sequence will be in ascending order. This means

- if you choose a column containing numeric data, it sorts the output from the smallest to largest. For example, if sorting on customerid, the ID numbers are sorted from smallest to largest.
    
- if the column contains alphabetic characters, such as in the example with the city column, it orders the records from the beginning of the alphabet to the end. 
    

### **Sorting in descending order**

You can also use the ORDER BY with the DESC keyword to sort in descending order. The DESC keyword is short for "descending" and tells SQL to sort numbers from largest to smallest, or alphabetically from Z to A. This can be done by following ORDER BY with the DESC keyword. For example, you can run this query to examine how the results differ when DESC is applied: 
``` SQL
SELECT customerid, city, country

FROM customers

ORDER BY city DESC;
```

Now, cities at the end of the alphabet are listed first.

### **Sorting based on multiple columns**

You can also choose multiple columns to order by. For example, you might first choose the country and then the city column. SQL then sorts the output by country, and for rows with the same country, it sorts them based on city. You can run this to explore how SQL displays this:

``` SQL
SELECT customerid, city, country

FROM customers

ORDER BY country, city;
```