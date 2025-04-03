# Basic SQL Cheat Sheet

## Syntax

<details>
<summary>Comment</summary>

<br/>

Comments can be used to add descriptive notes to the SQL. Comments are not executed.

<br/>

```sh
-- This is a single line comment

/*
This is a multiline comment
*/
```

<br/>

The statement below is commented out, so it wont be executed
```sh
-- SELECT * FROM Teachers
```

<br/>

</details>


<details>
<summary>CREATE</summary>

<br/>

The CREATE command is used to create tables.

<br/>

A Teacher table is created with a FullName column. The FullNames are defined as characters with a length of up to 50.

```sh
CREATE TABLE Teacher (
	FullName varchar(50),
	PRIMARY KEY (FullName)
);
```

<br/>

A Teacher table is created with a auto incrementing ID column and a FullName column. When a new row is inserted, it will be assigned an ID which will be 1 higher than the previously highest ID

```sh
CREATE TABLE Teacher (
    TeacherID INT AUTO_INCREMENT PRIMARY KEY,
    FullName VARCHAR(50) NOT NULL
);
```

<br/>

</details>


<details>
<summary>DROP</summary>

<br/>

The DROP command is used to delete tables.

<br/>

Deletes the Teacher table

```sh
DROP TABLE Teacher;
```

<br/>

</details>


<details>
<summary>INSERT</summary>

<br/>

The INSERT command is used to insert data into tables.

<br/>

Five rows are inserted into the Teacher table. Each row has a FullName value.

```sh
INSERT INTO Teacher (FullName)
VALUES 	('John Black'),
		('Jussi Blue'),
		('Sarah White'),
		('Karin Grey'),
		('Gary Green');
```

<br/>

</details>


<details>
<summary>SELECT</summary>

<br/>

The SELECT command is used to view the data inside tables.

<br/>

Returns the entire Teacher table, including the column names and all the data inside.

```sh
SELECT * FROM Teacher
```

<br/>

Returns the entire Teacher table, sorted by the FullName A-Z 

```sh
SELECT *
FROM Teacher
ORDER by FullName 
```

<br/>

</details>
