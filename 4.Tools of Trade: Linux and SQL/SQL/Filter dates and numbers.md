The three common data types that you will find in databases: *string*, *numeric*, and *date and time*. **String data** is data consisting of an ordered sequence of characters. These characters could be numbers, letters, or symbols. For example, you'll encounter string data in user names, such as a user name: analyst10. **Numeric data** is data consisting of numbers, such as a count of log-in attempts. Unlike strings, mathematical operations can be used on numeric data, like multiplication or addition. **Date and time data** refers to data representing a date and/or time. 
Common operators for working with numeric or date and time data types include: equals, greater than, less than, not equal to, greater than or equal to, and less than or equal to. Let's say you want to find the log-in attempts made after 6 pm. Because this is past normal business hours, you want to look for suspicious patterns. You can identify these attempts by using the greater than operator in your filter. 
We can also filter for numbers and dates by using the BETWEEN operator. **BETWEEN** is an operator that filters for numbers or dates within a range. An example of this would be when looking for all patches installed within a certain range. 
*Note: When we filter for strings, dates, and times, we use quotation marks to specify what we're looking for. However, for numbers, we don't use quotation marks. *


## Numbers, dates, and times in cybersecurity

Security analysts work with more than just **string data**, or data consisting of an ordered sequence of characters. 

They also frequently work with **numeric data**, or data consisting of numbers. A few examples of numeric data that you might encounter in your work as a security analyst include:

- the number of login attempts
    
- the count of a specific type of log entry
    
- the volume of data being sent from a source
    
- the volume of data being sent to a destination
    

You'll also encounter **date and time data**, or data representing a date and/or time. As a first example, logs will generally timestamp every record. Other time and date data might include:

- login dates
    
- login times
    
- dates for patches 
    
- the duration of a connection
    

## Comparison operators

In SQL, filtering numeric and date and time data often involves operators. You can use the following operators in your filters to make sure you return only the rows you need:

|**operator**|**use**|
|---|---|
|<|less than|
|>|greater than|
|=|equal to|
|<=|less than or equal to|
|>=|greater than or equal to|
|<>|not equal to|

**Note:** You can also use != as an alternative operator for not equal to.

### Incorporating operators into filters

These comparison operators are used in the WHERE clause at the end of a query. The following query uses the > operator to filter the birthdate column. You can run this query to explore its output:

```SQL
SELECT firstname, lastname, birthdate

FROM employees

WHERE birthdate > '1970-01-01';
```

This query returns the first and last names of employees born after, but not on, '1970-01-01' (or January 1, 1970). If you were to use the >= operator instead, the results would also include results on exactly '1970-01-01'.

In other words, the > operator is exclusive and the >= operator is inclusive.  An **exclusive operator** is an operator that does not include the value of comparison. An **inclusive operator** is an operator that includes the value of comparison.

### **BETWEEN**

Another operator used for numeric data as well as date and time data is the BETWEEN operator. BETWEEN filters for numbers or dates within a range. For example, if you want to find the first and last names of all employees hired between January 1, 2002 and January 1, 2003, you can use the BETWEEN operator as follows:

```SQL
SELECT firstname, lastname, hiredate

FROM employees

WHERE hiredate BETWEEN '2002-01-01' AND '2003-01-01';
```
**Note:** The BETWEEN operator is inclusive. This means records with a hiredate of January 1, 2002 or January 1, 2003 are included in the results of the previous query.

