# Querries

## Introduction

**We should get acquainted with the movies table.**

```shell
SELECT * FROM movies;
```

## Select

**Let’s only select the name and genre columns of the table.**

```shell
SELECT name, genre 
FROM movies;
```

**Now we want to include a third column.
Edit your query so that it returns the name, genre, and year columns of the table.**

```shell
SELECT name, genre, year 
FROM movies;

```

## As

**To showcase what the AS keyword does, select the name column and rename it with an alias of your choosing.**

```shell
SELECT name AS 'Movie'
FROM movies;
```

**Edit the query so that instead of selecting and renaming the name column, select the imdb_rating column and rename it as IMDb.**

```shell
SELECT imdb_rating AS 'IMDb'
FROM movies;
```

## Distinct

**What are the unique genres?**

```shell
SELECT DISTINCT genre 
FROM movies;
```

**Now, change the code so we return the unique values of the year column instead.**

```shell
SELECT DISTINCT year 
FROM movies;
```

## Where

**Suppose we want to take a peek at all the not-so-well-received movies in the database.**

```shell
SELECT * 
FROM movies 
WHERE imdb_rating < 5;
```

**Now retrieve all the recent movies, specifically those that were released after 2014.**

```shell
SELECT *
FROM movies
WHERE year > 2014;
```

## Like I

**Let’s test it out.**

```shell
SELECT * 
FROM movies
WHERE name LIKE 'Se_en';
```

## Like II

**How many movie titles contain the word ‘man’?**

```shell
SELECT * 
FROM movies
WHERE name LIKE '%man%';
```

**Edit the query so that it selects all the information about the movie titles that begin with the word ‘The’.**

```shell
SELECT * 
FROM movies
WHERE name LIKE 'The %';
```

## Is Null

**Write a query to find all the movies without an IMDb rating.
Select only the name column!**

```shell
SELECT name
FROM movies
WHERE imdb_rating IS NULL;
```

## Between

**Using the BETWEEN operator, write a query that selects all information about movies whose name begins with the letters ‘D’, ‘E’, and ‘F’.**

```shell
SELECT *
FROM movies
WHERE name BETWEEN 'D' AND 'G';
```

**Using the BETWEEN operator, write a new query that selects all information about movies that were released from the year 1970 up to and including 1979.**

```shell
SELECT *
FROM movies
WHERE year BETWEEN 1970 AND 1979;
```

## And

**Now, let’s retrieve every movie released in the 70’s, that’s also well received.**

```shell
SELECT *
FROM movies
WHERE year BETWEEN 1970 AND 1979
  AND imdb_rating > 8;
```
**Using AND, write a new query that selects all movies made prior to 1985 that are also in the horror genre.**

```shell
SELECT *
FROM movies
WHERE year < 1985
   AND genre = 'horror';
```

## Or

**Let’s test this out:**

```shell
SELECT *
FROM movies
WHERE year > 2014
   OR genre = 'action';
```

**Using OR, write a query that returns all movies that are either a romance or a comedy.**

```shell
SELECT *
FROM movies
WHERE genre = 'romance'
   OR genre = 'comedy';
```

## Order By

**Suppose we want to retrieve the name and year columns of all the movies, ordered by their name alphabetically.**

```shell
SELECT name, year
FROM movies
ORDER BY name;
```

**Write a new query that retrieves the name, year, and imdb_rating columns of all the movies, ordered highest to lowest by their ratings.**

```shell
SELECT name, year, imdb_rating
FROM movies
ORDER BY imdb_rating DESC;
```

## Limit

**Combining your knowledge of LIMIT and ORDER BY, write a query that returns the top 3 highest rated movies.
Select all the columns.**

```shell
SELECT *
FROM movies
ORDER BY imdb_rating DESC
LIMIT 3;
```

## Case

**Select the name column and use a CASE statement to create the second column that is:
‘Chill’ if genre = 'romance'
‘Chill’ if genre = 'comedy'
‘Intense’ in all other cases
Optional: Rename the whole CASE statement to ‘Mood’ using AS.**

```shell
SELECT name,
 CASE
  WHEN genre = 'romance' THEN 'Chill'
  WHEN genre = 'comedy'  THEN 'Chill'
  ELSE 'Intense'
 END AS 'Mood'
FROM movies;
```

# Project: New York Restaurants

## Task 1

**Start by getting a feel for the nomnom table:
What are the column names?**

```shell
SELECT *
FROM nomnom;
```

## Task 2

**What are the distinct neighborhoods?**

```shell
SELECT DISTINCT neighborhood
FROM nomnom;
```

## Task 3

**What are the distinct cuisine types?**

```shell
SELECT DISTINCT cuisine
FROM nomnom;
```

## Task 4

**Suppose we would like some Chinese takeout.
What are our options?**

```shell
SELECT *
FROM nomnom
WHERE cuisine = 'Chinese';
```

## Task 5

**Return all the restaurants with reviews of 4 and above.**

```shell
SELECT *
FROM nomnom
WHERE review >= 4;
```

## Task 6

**Suppose Abbi and Ilana want to have a fancy dinner date.
Return all the restaurants that are Italian and $$$.**

```shell
SELECT *
FROM nomnom
WHERE cuisine = 'Italian'
   AND price = '$$$';
```

## Task 7

**Your coworker Trey can’t remember the exact name of a restaurant he went to but he knows it contains the word ‘meatball’ in it.
Can you find it for him using a query?**

```shell
SELECT *
FROM nomnom
WHERE name LIKE '%meatball%';
```

## Task 8

**Let’s order delivery to the house!
Find all the close by spots in Midtown, Downtown or Chinatown.**

```shell
SELECT *
FROM nomnom
WHERE neighborhood = 'Midtown'
   OR neighborhood = 'Downtown'
   OR neighborhood = 'Chinatown'; 
```

## Task 9

**Find all the health grade pending restaurants (empty values).**

```shell
SELECT *
FROM nomnom
WHERE health IS NULL;
```

## Task 10

**Create a Top 10 Restaurants Ranking based on reviews.**

```shell
SELECT *
FROM nomnom
ORDER BY review DESC
LIMIT 10;
```

## Task 11

**Use a CASE statement to change the rating system to:
review > 4.5 is Extraordinary
review > 4 is Excellent
review > 3 is Good
review > 2 is Fair
Everything else is Poor
Don’t forget to rename the new column!**

```shell
SELECT name,
 CASE
  WHEN review > 4.5 THEN 'Extraordinary'
  WHEN review > 4 THEN 'Excellent'
  WHEN review > 3 THEN 'Good'
  WHEN review > 2 THEN 'Fair'
  ELSE 'Poor'
 END AS 'Review'
FROM nomnom;
```
