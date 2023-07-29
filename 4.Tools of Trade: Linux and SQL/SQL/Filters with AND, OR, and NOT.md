When working with real security questions, we often have to filter for multiple conditions. Vulnerabilities, for instance, might depend on more than one factor. For example, a security vulnerability might be related to machines using a specific email client on a specific operating system. So, to find the possible vulnerabilities, we need to find machines using both the email client and the operating system.
To make a query with multiple conditions that must be met, we use the AND operator between two separate conditions. **AND** is an operator that specifies that both conditions must be met simultaneously. 
The **OR** operator is an operator that specifies that either condition can be met. In a Venn diagram, let's say each circle represents a condition. When they are joined with OR, SQL would select all rows that satisfy one of the conditions. And it's also ok if it meets both conditions.
The **NOT** operator negates a condition. In a diagram, we can show this by selecting every entry that does not match our condition. The condition is represented by the circle. The filled-in portion outside the circle represents what gets returned. This is all data that does not match the condition. For example, when picking out fruit, you can be looking for any fruit that is not an apple. That is a lot more efficient than telling your friend you want a banana or an orange or a lime, and so on.

## Logical operators

AND, OR, and NOT allow you to filter your queries to return the specific information that will help you in your work as a security analyst. They are all considered logical operators.

### AND

First, AND is used to filter on two conditions. AND specifies that both conditions must be met simultaneously. 

As an example, a cybersecurity concern might affect only those customer accounts that meet both the condition of being handled by a support representative with an ID of 5 and the condition of being located in the USA. To find the names and emails of those specific customers, you should place the two conditions on either side of the AND operator in the WHERE clause:

```SQL
SELECT firstname, lastname, email, country, supportrepid

FROM customers

WHERE supportrepid = 5 AND country = 'USA';
```

Running this query returns four rows of information about the customers. You can use this information to contact them about the security concern.

### OR

The OR operator also connects two conditions, but OR specifies that either condition can be met. It returns results where the first condition, the second condition, or both are met.

For example, if you are responsible for finding all customers who are either in the USA or Canada so that you can communicate information about a security update, you can use an OR operator to find all the needed records. As the following query demonstrates, you should place the two conditions on either side of the OR operator in the WHERE clause:

```SQL
SELECT firstname, lastname, email, country

FROM customers

WHERE country = 'Canada' OR country = 'USA';
```


The query returns all customers in either the US or Canada.

**Note:** Even if both conditions are based on the same column, you need to write out both full conditions. For instance, the query in the previous example contains the filter WHERE country = 'Canada' OR country = 'USA'.

### NOT

Unlike the previous two operators, the NOT operator only works on a single condition, and not on multiple ones. The NOT operator negates a condition. This means that SQL returns all records that don’t match the condition specified in the query. 

For example, if a cybersecurity issue doesn't affect customers in the USA but might affect those in other countries, you can return all customers who are not in the USA. This would be more efficient than creating individual conditions for all of the other countries. To use the NOT operator for this task, write the following query and place NOT directly after WHERE:

```SQL
SELECT firstname, lastname, email, country

FROM customers

WHERE NOT country = 'USA';
```


SQL returns every entry where the customers are not from the USA.

**Pro tip:** Another way of finding values that are not equal to a certain value is by using the <> operator or the != operator. For example, WHERE country <> 'USA' and WHERE country != 'USA' are the same filters as WHERE NOT country = 'USA'.

## Combining logical operators

Logical operators can be combined in filters. For example, if you know that both the USA and Canada are not affected by a cybersecurity issue, you can combine operators to return customers in all countries besides these two. In the following query, NOT is placed before the first condition, it's joined to a second condition with AND, and then NOT is also placed before that second condition. You can run it to explore what it returns:

```SQL
SELECT firstname, lastname, email, country

FROM customers

WHERE NOT country = 'Canada' AND NOT country = 'USA';
```