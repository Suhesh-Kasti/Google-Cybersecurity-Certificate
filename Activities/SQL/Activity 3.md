## Task 1. Retrieve login attempts after a certain date

In this task, you need to investigate a recent security incident. To do this, you need to gather information about login attempts made after a certain date.

1. Complete the SQL query to retrieve data for login attempts made after `'2022-05-09'`. Replace `X` with the correct operator:

SELECT * 
FROM log_in_attempts 
WHERE login_date X '2022-05-09';

The correct query to solve this step:

```SQL
SELECT * FROM 
log_in_attempts 
WHERE login_date > '2022-05-09';
```

How many login attempts were made after 2022-05-09?
**Answer**: The number of login attempts made after the 2022-05-09 is 125.

**Now**, based on your first query, you find a need to expand the date range to include 2022-05-09 in your search.

2. Complete the SQL query to retrieve data for login attempts that were made on or after `'2022-05-09'`. Replace `X` with the correct operator:

SELECT * 
FROM log_in_attempts 
WHERE login_date X '2022-05-09';

The correct query to solve this step:

```SQL
SELECT * 
FROM log_in_attempts 
WHERE login_date >= '2022-05-09';
```


How many login attempts were made on or after 2022-05-09?
**Answer**: The number of login attempts made from 2022-05-09 onward is 165.

## Task 2. Retrieve logins in a date range

In this task, you need to narrow the focus of the search. Login attempts made after 2022-05-11 shouldn't be included. Use the `BETWEEN` and `AND` operators to return results between `'2022-05-09'` and `'2022-05-11'`.

- Run the query to retrieve the required records. You must insert the required dates `X` and `Y`:

SELECT * 
FROM log_in_attempts 
WHERE login_date BETWEEN 'X' AND 'Y';

The correct query to solve this step:

```SQL
SELECT * 
FROM log_in_attempts 
WHERE login_date BETWEEN '2022-05-09' AND '2022-05-11';
```


How many login attempts were made between 2022-05-09 and 2022-05-11?
**Answer**: 123 login attempts were made between 2022-05-09 and 2022-05-11.


## Task 3. Investigate logins at certain times

In this task, you need to investigate logins that were made at certain times. To do this, filter the data in the `log_in_attempts` table by login time (`login_time`).

**First**, your organization's typical work hours begin at 07:00:00. Retrieve all login attempts made before 07:00:00 to learn more about the users who are logging in outside of typical hours.

1. Write a SQL query to retrieve data for login attempts made before `'07:00:00'`.

_**Note:** Place time data in single quotation marks._

The correct query to solve this step:

```SQL
SELECT * 
FROM log_in_attempts 
WHERE login_time < '07:00:00';
```


What is the username of the fifth record returned from this query?
**Answer**: The username in the fifth record returned from this query is eraab.

2. Modify the query to return logins between `'06:00:00'` and `'07:00:00'`.

The correct query to solve this step:

```SQL
SELECT * 
FROM log_in_attempts 
WHERE login_time BETWEEN '06:00:00' AND '07:00:00';
```


What time was the earliest login attempt between 06:00:00 and 07:00:00?
**Answer**: The earliest login attempt was at 06:01:31.


## Task 4. Investigate logins by event ID

In this task, you need to investigate login attempts based on event ID numbers. With this query, you want to return only the `event_id`, `username`, and `login_date` fields from the `log_in_attempts` table.

_**Note:** The `event_id` column contains numeric data; do not place numeric data in quotation marks._

1. Write a query to return login attempts with `event_id` greater than or equal to `100`.

The correct query to solve this step:

```SQL
SELECT event_id, username, login_date 
FROM log_in_attempts 
WHERE event_id >= 100;
```

What is the login date of the third result returned by your query?
**Answer**: The login date of the third result returned is 2022-05-09.

2. Modify the query to return only login attempts with `event_id` between `100` and `150`.

The correct query to solve this step:

```SQL
SELECT event_id, username, login_date
FROM log_in_attempts 
WHERE event_id BETWEEN 100 AND 150;
```

What is the username of the seventh result returned by your query?
**Answer**: The username of the seventh result is tmitchel.