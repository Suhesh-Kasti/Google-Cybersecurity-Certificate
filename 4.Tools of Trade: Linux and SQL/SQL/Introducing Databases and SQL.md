## Database
**Database** as an organized collection of information or data. Databases are often compared to spreadsheets. While these programs are convenient ways to store data, spreadsheets are often designed for a single user or a small team to store less data. In contrast, *databases can be accessed by multiple people simultaneously* and can store massive amounts of data. Databases can also perform complex tasks while accessing data. 
For example, these could be databases containing information on login attempts, software and updates, or machines and their owners. Using databases allow us to store large amounts of data while keeping it quick and easy to access.

A **relational database** is a structured database containing tables that are related to each other. Each table contains fields of information. For example, in this table on employees, these would include fields like employee_id, device_id, and username.
These are the columns of the tables. In addition, tables contain rows also called **records**. Rows are filled with specific data related to the columns in the table. 

Relational databases often have multiple tables. Consider an example where we have two tables from a larger database, one with employees of the company and another with machines given to those employees. *We can connect two tables if they share a common column.*
The columns that relate two tables to each other are called **keys**. There are two types of keys. 
1. **Primary key**
The primary key refers to a column where every row has a unique entry. The primary key must not have any duplicate values, or any null or empty values. The primary key allows us to uniquely identify every row in our table. For the table of employees, employee_id is a primary key. Every employee_id is unique and there are no employee_ids that are duplicate or empty.
2. **Foreign key**
The foreign key is a column in a table that is a primary key in another table. Foreign keys, unlike primary keys, can have empty values and duplicates. The foreign key allows us to connect two tables together. In our example, we can look at the employee_id column in the machines table. We previously identified this as a primary key in the employees table, so we can use this to connect every machine to their corresponding employee.

*It's also important to know that a table can only have one primary key, but multiple foreign keys.*


## SQL
S-Q-L, stands for *Structured Query Language*. **SQL** is a programming language used to create, interact with, and request information from a database.
A **query** is a request for data from a database table or a combination of tables. Nearly all relational databases rely on some version of SQL to query data. The different versions of SQL only have slight differences in their structure, like where to place quotation marks. 
A **log** is a record of events that occur within an organization's systems. For example, some logs might contain details on machines used in a company, and as an analyst, you would need to find those machines that weren't configured properly. Other logs might describe the visitors to your website or web app and the tasks they perform. In that case, you might be looking for unusual patterns that may point to malicious activity. *Security logs are often very large and hard to process*. There are millions of data points, and it's very time consuming to find what you need. But this is where SQL comes in! It can search through millions of data points to extract relevant rows of data using one query that takes seconds to run. 

SQL is also a very common language used for basic data analytics.We can use SQL's filtering to find data to support security-related decisions and analyze when things may go wrong. For instance, we can identify what machines haven't received the latest patch. This is important because patches are updates that help secure against attacks. As another example, you can use SQL to determine the best time to update a machine based on when it's least used.

# SQL filtering versus Linux filtering

Previously, you explored the Linux commands that allow you to filter for specific information contained within files or directories. And, more recently, you examined how SQL helps you efficiently filter for the information you need. In this reading, you'll explore differences between the two tools as they relate to filtering. You'll also learn that one way to access SQL is through the Linux command line.

## Accessing SQL

There are many interfaces for accessing SQL and many different versions of SQL. One way to access SQL is through the Linux command line.

To access SQL from Linux, you need to type in a command for the version of SQL that you want to use. For example, if you want to access SQLite, you can enter the command sqlite3 in the command line.

After this, any commands typed in the command line will be directed to SQL instead of Linux commands.

## Differences between Linux and SQL filtering 

Although both Linux and SQL allow you to filter through data, there are some differences that affect which one you should choose.

### **Structure**

SQL offers a lot more structure than Linux, which is more free-form and not as tidy.

For example, if you wanted to access a log of employee log-in attempts, SQL would have each record separated into columns. Linux would print the data as a line of text without this organization. As a result, selecting a specific column to analyze would be easier and more efficient in SQL.

In terms of structure, SQL provides results that are more easily readable and that can be adjusted more quickly than when using Linux.

### **Joining tables**

Some security-related decisions require information from different tables. SQL allows the analyst to join multiple tables together when returning data. Linux doesn’t have that same functionality; it doesn’t allow data to be connected to other information on your computer. This is more restrictive for an analyst going through security logs.

### **Best uses**

As a security analyst, it’s important to understand when you can use which tool. Although SQL has a more organized structure and allows you to join tables, this doesn’t mean that there aren’t situations that would require you to filter data in Linux.

A lot of data used in cybersecurity will be stored in a database format that works with SQL. However, other logs might be in a format that is not compatible with SQL. For instance, if the data is stored in a text file, you cannot search through it with SQL. In those cases, it is useful to know how to filter in Linux.