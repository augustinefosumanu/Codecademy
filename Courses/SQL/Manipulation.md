# Course

## Create

**Confirm no celebs table exists by entering the following in the code editor:**

```shell
 select *
 from celebs;
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

## 

****

```shell

```
