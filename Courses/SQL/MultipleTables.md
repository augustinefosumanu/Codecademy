# Multiple Tables

## Introduction

**Examine these tables:
orders, subscriptions, customers**

```shell
SELECT *
FROM orders
LIMIT 5;

SELECT *
FROM subscriptions
LIMIT 5;

SELECT * 
FROM customers
LIMIT 5;
```

## Combining Tables Manually

**Using the tables displayed, what is the description of the magazine ordered in order_id 1?**

```shell
Sports Magazine
```

**Using the tables displayed, what is the customer_name of the customer in order_id 3?**

```shell
Joe Schmo
```

## Combining Tables with SQL

**Join orders table and subscriptions table and select all columns.
Make sure to join on the subscription_id column.**

```shell
SELECT *
FROM orders
JOIN subscriptions
  ON orders.subscription_id = subscriptions.subscription_id;
```

**Don’t remove the previous query.
Add a second query after your first one that only selects rows from the join where description is equal to ‘Fashion Magazine’.**

```shell
SELECT *
FROM orders
JOIN subscriptions
  ON orders.subscription_id = subscriptions.subscription_id
WHERE subscriptions.description = 'Fashion Magazine';
```

## Inner Joins

**Suppose we are working for The Codecademy Times, a newspaper with two types of subscriptions:
print newspaper
online articles
Some users subscribe to just the newspaper, some subscribe to just the online edition, and some subscribe to both.
There is a newspaper table that contains information about the newspaper subscribers.
Count the number of subscribers who get a print newspaper using COUNT().**

```shell
SELECT COUNT(*)
FROM newspaper;
```

**Don’t remove your previous query.
There is also an online table that contains information about the online subscribers.
Count the number of subscribers who get an online newspaper using COUNT().**

```shell
SELECT COUNT(*)
FROM newspaper;
```

**Don’t remove your previous queries.
Join newspaper table and online table on their id columns (the unique ID of the subscriber).
How many rows are in this table?**

```shell
SELECT COUNT(*)
FROM newspaper
JOIN online
  ON newspaper.id = online.id;
```

## Left Joins

**Let’s return to our newspaper and online subscribers.
Suppose we want to know how many users subscribe to the print newspaper, but not to the online.
Start by performing a left join of newspaper table and online table on their id columns and selecting all columns.**

```shell
SELECT *
FROM newspaper
LEFT JOIN online
  ON newspaper.id = online.id;
```

**In order to find which users do not subscribe to the online edition, we need to add a WHERE clause.
Add a second query after your first one that adds the following WHERE clause and condition:**

```shell
SELECT *
FROM newspaper
LEFT JOIN online
  ON newspaper.id = online.id
WHERE online.id IS NULL;
```

## Primary Key vs Foreign Key

**Perform an inner join of classes and students using the primary and foreign keys described above, and select all the columns.**

```shell
SELECT *
FROM classes
JOIN students
  ON classes.id = students.class_id;
```

## Cross Join

**Let’s start by counting the number of customers who were subscribed to the newspaper during March.
Use COUNT(*) to count the number of rows and a WHERE clause to restrict to two conditions:
start_month <= 3
end_month >= 3**

```shell
SELECT COUNT(*)
FROM newspaper
WHERE start_month <= 3 
  AND end_month >= 3;
```

**The previous query lets us investigate one month at a time. In order to check across all months, we’re going to need to use a cross join.
Our database contains another table called months which contains the numbers between 1 and 12.
Select all columns from the cross join of newspaper and months.**

```shell
SELECT *
FROM newspaper
CROSS JOIN months;
```

**Create a third query where you add a WHERE statement to your cross join to restrict to two conditions:
start_month <= month
end_month >= month
This will select all months where a user was subscribed.**

```shell
SELECT *
FROM newspaper
CROSS JOIN months
WHERE start_month <= month
  AND end_month >= month;
```

**Create a final query where you aggregate over each month to count the number of subscribers.**

```shell
SELECT month,
   COUNT(*)
FROM newspaper
CROSS JOIN months
WHERE start_month <= month 
   AND end_month >= month
GROUP BY month;
```

## Union

**Let’s return to our newspaper and online subscriptions. We’d like to create one big table with both sets of data.
Use UNION to stack the newspaper table on top of the online table.**

```shell
SELECT * 
FROM newspaper 
UNION 
SELECT * 
FROM online;
```

## With

**Join the temporary table previous_query with customers table and select the following columns:
customers.customer_name
previous_query.subscriptions**

```shell
WITH previous_query AS (
   SELECT customer_id,
      COUNT(subscription_id) AS 'subscriptions'
   FROM orders
   GROUP BY customer_id
)
SELECT customers.customer_name, 
   previous_query.subscriptions
FROM previous_query
JOIN customers
  ON previous_query.customer_id = customers.customer_id;
```

# Project: Lyft Trip Data

## Task 1

**Let’s examine the three tables.**

```shell
SELECT * FROM trips;

SELECT * FROM riders;

SELECT * FROM cars;
```

## Task 2

**What’s the primary key of trips?
What’s the primary key of riders?
What’s the primary key of cars?**

```shell
The primary key of trips is id.

The primary key of riders is id.

The primary key of cars is id.
```

## Task 3

**Try out a simple cross join between riders and cars.
Is the result useful?**

```shell
SELECT riders.first,
   riders.last,
   cars.model
FROM riders, cars;

The result combines each user with every car model. Not so useful.
```

## Task 4

**Suppose we want to create a Trip Log with the trips and its users.
Find the columns to join between trips and riders and combine the two tables using a LEFT JOIN.
Let trips be the left table.**

```shell
SELECT *
FROM trips
LEFT JOIN riders 
  ON trips.rider_id = riders.id;
```

## Task 5

**Suppose we want to create a link between the trips and the cars used during those trips.
Find the columns to join on and combine the trips and cars table using an INNER JOIN.**

```shell
SELECT *
FROM trips
JOIN cars
  ON trips.car_id = cars.id;
```

## Task 6

**The new riders data are in! There are three new users this month.
Stack the riders table on top of the new table named riders2.**

```shell
SELECT *
FROM riders
UNION
SELECT *
FROM riders2;
```

## Task 7

**What is the average cost for a trip?**

```shell
SELECT ROUND(AVG(cost), 2)
FROM trips;
```

## Task 8

**
Lyft is looking to do an email campaign for all the irregular users.
Find all the riders who have used Lyft less than 500 times!**

```shell
SELECT *
FROM riders
WHERE total_trips < 500;
```

## Task 9

**Calculate the number of cars that are active.**

```shell
SELECT COUNT(*)
FROM cars
WHERE status = 'active';
```

## Task 10

**It’s safety recall time for cars that have been on the road for a while.
Write a query that finds the two cars that have the highest trips_completed.**

```shell
SELECT *
FROM cars
ORDER BY trips_completed DESC
LIMIT 2;
```
