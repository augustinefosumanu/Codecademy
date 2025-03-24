# Aggregate Functions

## Introduction

**Before getting started, take a look at the data in the fake_apps table.**

```shell
SELECT *
FROM fake_apps;
```

## Count

**Let’s count how many apps are in the table.**

```shell
SELECT COUNT(*) 
FROM fake_apps;
```

**Add a WHERE clause in the previous query to count how many free apps are in the table.**

```shell
SELECT COUNT(*) 
FROM fake_apps
WHERE price = 0;
```

## Sum

**Let’s find out the answer!**

```shell
SELECT SUM(downloads)
FROM fake_apps;
```

## Max / Min

**What is the least number of times an app has been downloaded?**

```shell
SELECT MIN(downloads)
FROM fake_apps;
```

**Write a new query that returns the price of the most expensive app.**

```shell
SELECT MAX(price)
FROM fake_apps;
```

## Average

**Calculate the average number of downloads for all the apps in the table.**

```shell
SELECT AVG(downloads)
FROM fake_apps;
```

**Write a new query that calculates the average price for all the apps in the table.**

```shell
 SELECT AVG(price)
 FROM fake_apps;
```

## Round

**Let’s return the name column and a rounded price column.**

```shell
SELECT name, ROUND(price, 0)
FROM fake_apps;
```

**In the last exercise, we were able to get the average price of an app ($2.02365) using this query:**

```shell
SELECT ROUND(AVG(price), 2)
FROM fake_apps;
```

## Group By I

**Here, our aggregate function is COUNT() and we arranged price into groups.**

```shell
SELECT price, COUNT(*) 
FROM fake_apps
GROUP BY price;
```

**In the previous query, add a WHERE clause to count the total number of apps that have been downloaded more than 20,000 times, at each price.**

```shell
SELECT price, COUNT(*) 
FROM fake_apps
WHERE downloads > 20000
GROUP BY price;
```

**Write a new query that calculates the total number of downloads for each category.
Select category and SUM(downloads).**

```shell
SELECT category, SUM(downloads)
FROM fake_apps
GROUP BY category;
```

## Group By II

**Write the exact query, but use column reference numbers instead of column names after GROUP BY.**

```shell
SELECT category, 
   price,
   AVG(downloads)
FROM fake_apps
GROUP BY 1, 2;
```

## Having

**Add a HAVING clause to restrict the query to price points that have more than 10 apps.**

```shell
SELECT price, 
   ROUND(AVG(downloads)),
   COUNT(*)
FROM fake_apps
GROUP BY price
HAVING COUNT(*) > 10;
```

# Project: Trends in Startups

## Task 1

**Getting started, take a look at the startups table:**

```shell
SELECT *
FROM startups;
```

## Task 2

**Calculate the total number of companies in the table.**

```shell
SELECT COUNT(*)
FROM startups;
```

## Task 3

**We want to know the total value of all companies in this table.
Calculate this by getting the SUM() of the valuation column.**

```shell
SELECT SUM(valuation)
FROM startups;
```

## Task 4

**What is the highest amount raised by a startup?
Return the maximum amount of money raised.**

```shell
SELECT MAX(raised)
FROM startups;
```

## Task 5

**Edit the query so that it returns the maximum amount of money raised, during ‘Seed’ stage.**

```shell
SELECT MAX(raised)
FROM startups
WHERE stage = 'Seed';
```

## Task 6

**In what year was the oldest company on the list founded?**

```shell
SELECT MIN(founded)
FROM startups;
```

## Task 7

**Return the average valuation.**

```shell
SELECT AVG(valuation)
FROM startups;
```

## Task 8

**Return the average valuation, in each category.**

```shell
SELECT category, AVG(valuation)
FROM startups
GROUP BY category;
```

## Task 9

**Return the average valuation, in each category.
Round the averages to two decimal places.**

```shell
SELECT category, ROUND(AVG(valuation), 2)
FROM startups
GROUP BY category;
```

## Task 10

**Return the average valuation, in each category.
Round the averages to two decimal places.
Lastly, order the list from highest averages to lowest.**

```shell
SELECT category, ROUND(AVG(valuation), 2)
FROM startups
GROUP BY 1
ORDER BY 2 DESC;
```

## Task 11

**First, return the name of each category with the total number of companies that belong to it.**

```shell
SELECT category, COUNT(*)
FROM startups
GROUP BY category;
```

## Task 12

**Next, filter the result to only include categories that have more than three companies in them.
What are the most competitive markets?**

```shell
SELECT category, COUNT(*)
FROM startups
GROUP BY category
HAVING COUNT(*) > 3
ORDER BY 2 DESC;
```

## Task 13

**What is the average size of a startup in each location?**

```shell
SELECT location, AVG(employees)
FROM startups
GROUP BY location;
```

## Task 14

**What is the average size of a startup in each location, with average sizes above 500?**

```shell
SELECT location, AVG(employees)
FROM startups
GROUP BY location
HAVING AVG(employees) > 500;
```

# Project: Analyze Hacker News Trends

## Task 1

**Start by getting a feel for the hacker_news table!
Let’s find the most popular Hacker News stories:**

```shell
SELECT title, score
FROM hacker_news
ORDER BY score DESC
LIMIT 5;
```

## Task 2

**First, find the total score of all the stories.**

```shell
SELECT SUM(score)
FROM hacker_news;
```

## Task 3

**Find the individual users who have gotten combined scores of more than 200, and their combined scores.
GROUP BY and HAVING are needed!**

```shell
SELECT user, SUM(score)
FROM hacker_news
GROUP BY user
HAVING SUM(score) > 200
ORDER BY 2 DESC;
```

## Task 4

**Then, we want to add these users’ scores together and divide by the total to get the percentage.
Add their scores together and divide it by the total sum. Like so:**

```shell
SELECT (517 + 309 + 304 + 282) / 6366.0;
```

## Task 5

**The url of the video is:
https://www.youtube.com/watch?v=dQw4w9WgXcQ
How many times has each offending user posted this link?**

```shell
SELECT user,
   COUNT(*)
FROM hacker_news
WHERE url LIKE '%watch?v=dQw4w9WgXcQ%'
GROUP BY user
ORDER BY COUNT(*) DESC;
```

## Task 6

**Hacker News stories are essentially links that take users to other websites.
Which of these sites feed Hacker News the most:
GitHub, Medium, or New York Times?**

```shell
SELECT CASE
   WHEN url LIKE '%github.com%' THEN 'GitHub'
   WHEN url LIKE '%medium.com%' THEN 'Medium'
   WHEN url LIKE '%nytimes.com%' THEN 'New York Times'
   ELSE 'Other'
  END AS 'Source'
FROM hacker_news;
```

## Task 7

**Next, build on the previous query:
Add a column for the number of stories from each URL using COUNT().
Also, GROUP BY the CASE statement.
Remember that you can refer to a column in GROUP BY using a number.**

```shell
SELECT CASE
   WHEN url LIKE '%github.com%' THEN 'GitHub'
   WHEN url LIKE '%medium.com%' THEN 'Medium'
   WHEN url LIKE '%nytimes.com%' THEN 'New York Times'
   ELSE 'Other'
  END AS 'Source',
  COUNT(*)
FROM hacker_news
GROUP BY 1;
```

## Task 8

**Every submitter wants their story to get a high score so that the story makes it to the front page, but…
What’s the best time of the day to post a story on Hacker News?**

```shell
SELECT timestamp
FROM hacker_news
LIMIT 10;
```

## Task 9

**SQLite comes with a strftime() function - a very powerful function that allows you to return a formatted date.
It takes two arguments:
strftime(format, column)**

```shell
SELECT timestamp,
   strftime('%H', timestamp)
FROM hacker_news
GROUP BY 1
LIMIT 20;
```

## Task 10

**Okay, now we understand how strftime() works. Let’s write a query that returns three columns:
The hours of the timestamp
The average score for each hour
The count of stories for each hour**

```shell
SELECT strftime('%H', timestamp), 
   AVG(score),
   COUNT(*)
FROM hacker_news
GROUP BY 1
ORDER BY 2 DESC;
```

## Task 11

**Let’s edit a few things in the previous query:
Round the average scores (ROUND()).
Rename the columns to make it more readable (AS).
Add a WHERE clause to filter out the NULL values in timestamp.
Take a look at the result again:
What are the best hours to post a story on Hacker News?**

```shell
SELECT strftime('%H', timestamp) AS 'Hour', 
   ROUND(AVG(score), 1) AS 'Average Score', 
   COUNT(*) AS 'Number of Stories'
FROM hacker_news
WHERE timestamp IS NOT NULL
GROUP BY 1
ORDER BY 2 DESC;
```
