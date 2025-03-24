# Course

## Create

**Confirm no celebs table exists by entering the following in the code editor:**

```shell
SELECT *
FROM celebs;
```
**Now that we know the database is empty, let’s create a new celebs table.**

```shell
 CREATE TABLE celebs (
   id INTEGER, 
   name TEXT, 
   age INTEGER
); 
```

## Insert

**Add a row to the table.**

```shell
INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 29);
```

**Add three more celebrities to the table.**

```shell
INSERT INTO celebs (id, name, age) 
VALUES (2, 'Beyonce Knowles', 42); 

INSERT INTO celebs (id, name, age) 
VALUES (3, 'Jeremy Lin', 35); 

INSERT INTO celebs (id, name, age) 
VALUES (4, 'Taylor Swift', 33); 
```

## Select

**Let’s take a closer look at SELECT and retrieve all the names in the celebs table.**

```shell
SELECT name FROM celebs; 
```

**Delete your previous SELECT statement from the code editor and SELECT all the data in the celebs table**

```shell
SELECT * FROM celebs;
```

## Alter

**Add a new column to the table.**

```shell
ALTER TABLE celebs 
ADD COLUMN twitter_handle TEXT; 

SELECT * FROM celebs; 
```

## Update

**Update the table to include Taylor Swift’s twitter handle.**

```shell
UPDATE celebs 
SET twitter_handle = '@taylorswift13' 
WHERE id = 4; 

SELECT * FROM celebs;
```

## Delete

**Delete all of the rows that have a NULL value in the twitter handle column.**

```shell
DELETE FROM celebs 
WHERE twitter_handle IS NULL;

SELECT * FROM celebs; 
```

## Constraints

**Create a new table with constraints on the values.**

```shell
CREATE TABLE awards (
   id INTEGER PRIMARY KEY,
   recipient TEXT NOT NULL,
   award_name TEXT DEFAULT 'Grammy'
);
```

# Project

## Task 1

**Create a table named friends with three columns:
id that stores INTEGER
name that stores TEXT
birthday that stores DATE**

```shell
CREATE TABLE friends(
  id INTEGER,
  name TEXT,
  birthday DATE
);
```

## Task 2

**Beneath your current code, add Ororo Munroe to friends.
Her birthday is May 30th, 1940.**

```shell
INSERT INTO friends(id, name, birthday)
VALUES(1, 'Ororo Munroe', 'May 30th 1940');
```

## Task 3

**Let’s make sure that Ororo has been added to the database:
Check for two things:
Is friends table created?
Is Ororo Munroe added to it?**

```shell
SELECT * 
FROM friends;
```

## Task 4

**Let’s move on!
Add two of your friends to the table.
Insert an id, name, and birthday for each of them.**

```shell
INSERT INTO friends(id, name, birthday)
VALUES(2, 'Musa Munroe', 'May 9th 1953');

INSERT INTO friends(id, name, birthday)
VALUES(3, 'Eva Munroe', 'May 4th 1965');
```

## Task 5

**Ororo Munroe just realized that she can control the weather and decided to change her name. Her new name is “Storm”.
Update her record in friends.**

```shell
UPDATE friends
SET name = 'Storm'
WHERE id = 1;
```

## Task 6

**Add a new column named email.**

```shell
ALTER TABLE friends
ADD COLUMN email TEXT;
```

## Task 7

**Update the email address for everyone in your table.
Storm’s email is storm@codecademy.com.**

```shell
UPDATE friends
SET email = 'storm@codecademy.com'
WHERE id = 1;
```

## Task 8

**Wait, Storm is fictional…
Remove her from friends.**

```shell
DELETE FROM friends
WHERE id = 1;
```

## Task 9

**Great job! Let’s take a look at the result one last time:**

```shell
SELECT * 
FROM friends;
```
