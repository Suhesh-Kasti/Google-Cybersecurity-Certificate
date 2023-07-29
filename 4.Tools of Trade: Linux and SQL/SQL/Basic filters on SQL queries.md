One of the most powerful features of SQL is its ability to filter. **Filtering** is selecting data that match a certain condition. Think of filtering as a way of only choosing the data we want. Let's say we wanted to select apples from a fruit cart. Filtering allows us to specify what kind of apples we want to choose. When we go buy apples, we might explicitly say, "Choose only apples that are fresh." This removes apples that aren't fresh from the selection. This is a filter! We might filter a log-in attempts table to find all attempts from a specific country. This could be done by applying a filter on the country column. For example, we could filter to just return records containing Canada.

An **operator** is a symbol or keyword that represents an operation. An example of an operator would be the *equal to* operator. 
For example, if we wanted to find all records that have USA in the country column, we use country = 'USA' To filter a query in SQL, we simply add an extra line to the SELECT and FROM statement we used before. This extra line will use a WHERE clause. In SQL, ***WHERE** indicates the condition for a filter*. After the keyword WHERE, the specific condition is listed using operators. So if we wanted to find all of the login attempts made in the United States, we would create this filter. 
We can also make our conditions more complex by searching for a pattern instead of an exact word. For example, we could search for records in column that match a certain pattern. Perhaps we might want all offices in the East building. To search for a pattern, we used the ***percentage sign*** to act as a wildcard for unspecified characters. If we ran a filter for 'East%', this would return all records that start with East -- for example, the offices East-120, East-290, and East-435.

When searching for patterns with the percentage sign, we cannot use the equals operator. Instead, we use another operator, LIKE. **LIKE** is an operator used with WHERE to search for a pattern in a column.
Since LIKE is an operator, similar to the equal sign, we use it instead of the equal sign. So, when our goal is to return all values in the office column that start with the word East, LIKE would appear in a WHERE clause.

# The WHERE clause and basic operators

## How filtering helps

In a cybersecurity context, we might use filters to find the login attempts of a specific user or all login attempts made at the time of a security issue. As another example, we might filter to find the devices that are running a specific version of an application.

## WHERE 

To create a filter in SQL, you need to use the keyword WHERE. WHERE indicates the condition for a filter.

If you needed to email employees with a title of IT Staff, we might use a query like 

```SQL
SELECT firstname, lastname, title, email

FROM employees

WHERE title = 'IT Staff';
```


Rather than returning all records in the employees table, this WHERE clause instructs SQL to return only those that contain 'IT Staff' in the title column. It uses the equals sign (=) operator to set this condition.

**Note:** You should place the semicolon (;) where the query ends. When you add a filter to a basic query, the semicolon is after the filter. 

## Filtering for patterns

You can also filter based on a pattern. For example, you can identify entries that start or end with a certain character or characters. Filtering for a pattern requires incorporating two more elements into your WHERE clause:

- a wildcard 
    
- the LIKE operator
    

### **Wildcards**

A **wildcard** is a special character that can be substituted with any other character. Two of the most useful wildcards are the percentage sign (%) and the underscore (\_):

- The percentage sign substitutes for any number of other characters. 
    
- The underscore symbol only substitutes for one other character.
    

These wildcards can be placed after a string, before a string, or in both locations depending on the pattern you’re filtering for.

The following table includes these wildcards applied to the string 'a' and examples of what each pattern would return.

|**Pattern**|**Results that could be returned**|
|---|---|
|'a%'|apple123, art, a|
|'a_'|as, an, a7|
|'a__'|ant, add, a1c|
|'%a'|pizza, Z6ra, a|
|'\_a'|ma, 1a, Ha|
|'%a%'|Again, back, a|
|'\_a_'|Car, ban, ea7|

### **LIKE**

To apply wildcards to the filter, you need to use the LIKE operator instead of an equals sign (=). LIKE is used with WHERE to search for a pattern in a column. 

For instance, if we want to email employees with a title of either 'IT Staff' or 'IT Manager', we can use LIKE operator combined with the % wildcard:  

```SQL
SELECT lastname, firstname, title, email

FROM employees

WHERE title LIKE 'IT%';

```
This query returns all records with values in the title column that start with the pattern of 'IT'. This means both 'IT Staff' and 'IT Manager' are returned.

As another example, if you want to search through the invoices table to find all customers located in states with an abbreviation of 'NY', 'NV', 'NS' or 'NT', you can use the 'N_' pattern on the state column:

```SQL
SELECT firstname,lastname, state, country

FROM customers

WHERE state LIKE 'N_';
```
This returns all the records with state abbreviations that follow this pattern.