## Task 1. Retrieve employee device data

The information we need is in the `machines` table in the `organization` database.

**First**, you need to retrieve all the information about the employee devices.

1. Run the following query to select all device information from the `machines` table:

SELECT *
FROM machines;

_**Note:** Using the asterisk (`*`) returns all data from the specified table. Also, table names in MySQL are case-sensitive._

The output returns all the contents of the `machines` table:

+--------------+------------------+----------------+---------------+-------------+
| device_id    | operating_system | email_client   | OS_patch_date | employee_id |
+--------------+------------------+----------------+---------------+-------------+
| a184b775c707 | OS 1             | Email Client 1 | 2021-09-01    |        1156 |
| a192b174c940 | OS 2             | Email Client 1 | 2021-06-01    |        1052 |
| a305b818c708 | OS 3             | Email Client 2 | 2021-06-01    |        1182 |
| a317b635c465 | OS 1             | Email Client 2 | 2021-03-01    |        1130 |
| a320b137c219 | OS 2             | Email Client 2 | 2021-03-01    |        1000 |
|...           |                  |                |               |             |
+--------------+------------------+----------------+---------------+-------------+
200 rows in set (0.356 sec)

**Next**, you want to focus on the email client running on various devices.

2. Run the following query to select only the `device_id` and `email_client` columns from the `machines` table. Replace `X` with `device_id` and `Y` with `email_client`:

SELECT X, Y FROM machines;

The correct query to solve this step:

SELECT device_id, email_client
FROM machines;

The output should return only the selected columns of the `machines` table:

+--------------+----------------+
| device_id    | email_client   |
+--------------+----------------+
| a184b775c707 | Email Client 1 |
| a192b174c940 | Email Client 1 |
| a305b818c708 | Email Client 2 |
| a317b635c465 | Email Client 2 |
| a320b137c219 | Email Client 2 |
|...           |                |
+--------------+----------------+
200 rows in set (0.015 sec)

What email client is returned in the third row?

**Answer**: The email client returned in the third row is Email Client 2.

**Now**, you need information on the operating systems used on various devices and their last patch date.

3. Complete the query to return only the `device_id`, `operating_system`, and `OS_patch_date` columns from the `machines` table. Replace `X`, `Y`, and `Z` with the columns that you need to return:

SELECT X, Y, Z FROM machines;

The correct query to solve this step:

SELECT device_id, operating_system, OS_patch_date
FROM machines;

What is the patch date of the first entry?
**Answer**: The patch date of the first entry is 2021-09-01.


## Task 2. Investigate login activity

In this task, you need to analyze the information from the `log_in_attempts` table to determine if any unusual activity has occurred.

**First**, you need to investigate the locations where login attempts were made to ensure that they’re in expected areas (the United States, Canada, or Mexico).

1. Write a SQL query to select the `event_id` and `country` columns from the `log_in_attempts` table.

The correct query to solve this step:

SELECT event_id, country
FROM log_in_attempts;

Were any login attempts made from Australia?
**Answer**: No. Login attempts were not made from Australia.

**Next**, you need to check if login attempts were made outside of the organization's working hours.

2. Write a SQL query that selects the `username`, `login_date`, and `login_time` columns from the `log_in_attempts` table.

The correct query to solve this step:

SELECT username, login_date, login_time
FROM log_in_attempts;


What username is returned in the fifth row?
**Answer**: The username returned in the fifth row is jrafael.

**Now**, you need to get a complete picture of all login attempts.

3. Write a SQL query that selects all columns from the `log_in_attempts` table, using a single symbol after the `SELECT` keyword.

The correct query to solve this step:

SELECT *
FROM log_in_attempts;

## Task 3. Order login attempts data

In this task, you need to use the `ORDER BY` keyword. You'll sequence the data that your query returns according to the login date and time.

**First**, you need to sort the information by date.

1. Run the following query, which orders `log_in_attempts` data by `login_date`:

SELECT *
FROM log_in_attempts
ORDER BY login_date;
What are the username and login date of the first record returned?
**Answer**: The first record returned contains a username of ivelasco and a login date of 2022-05-08.

**Now**, you need to further organize the previous results by ordering them by `login_time`.

2. Modify the query from the previous step by adding the login time to the `ORDER BY` clause. You must replace `X` with the appropriate column name:

SELECT * 
FROM log_in_attempts
ORDER BY login_date, X;

The correct query to solve this step:

SELECT *
FROM log_in_attempts
ORDER BY login_date, login_time;

What are the username and login time of the first record returned by the above query?
**Answer**: The first record returned contains a username of bsand and a login time of 00:19:11.