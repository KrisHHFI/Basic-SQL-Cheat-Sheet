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

A Teacher table is created with a TeacherName column. The TeacherNames are defined as characters with a length of up to 50.

```sh
CREATE TABLE Teacher (
	TeacherName varchar(50),
	PRIMARY KEY (TeacherName)
);
```

<br/>

A Teacher table is created with a auto incrementing ID column and a TeacherName column. When a new row is inserted, it will be assigned an ID which will be 1 higher than the previously highest ID

```sh
CREATE TABLE Teacher (
    TeacherID INT AUTO_INCREMENT PRIMARY KEY,
    TeacherName VARCHAR(50) NOT NULL
);
```
<br/>

A Student table is created, with the TeacherID linking it as a foreign key to the Teacher table

```sh
CREATE TABLE Student (
    StudentID INT AUTO_INCREMENT PRIMARY KEY,
    StudentName VARCHAR(50) NOT NULL,
    TeacherID INT,
    FOREIGN KEY (TeacherID) REFERENCES Teacher(TeacherID) ON DELETE SET NULL
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

Five rows are inserted into the Teacher table. Each row has a TeacherName value.

```sh
INSERT INTO Teacher (TeacherName)
VALUES 	('John Black'),
		('Jussi Blue'),
		('Sarah White'),
		('Karin Grey'),
		('Gary Green');
```

<br/>

Students are inserted into the Student table. Each student row has a StudentName value and a TeacherID (which references their teacher).
```sh
INSERT INTO Student (StudentName, TeacherID)
VALUES 
    ('Alice Brown', 2),  
    ('Bob Gray', 4),     
    ('Charlie Black', 1),
    ('Diana Green', 5),  
    ('Eva White', 3),    
    ('Frank Blue', 4),   
    ('Grace Yellow', 2), 
    ('Hannah Purple', 1),
    ('Iris Red', 5),     
    ('Jack Orange', 3);  
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

Returns the entire Teacher table, sorted by the TeacherName A-Z 

```sh
SELECT *
FROM Teacher
ORDER by TeacherName 
```

<br/>

Returns the entire Student table, sorted by the TeacherID 

```sh
SELECT *
FROM Student
ORDER by TeacherID
```

<br/>

Returns the students whose teacher's ID is 5

```sh
SELECT *
FROM Student
WHERE TeacherID = 5
```
<br/>

The SELECT and INNER JOIN statement is used to view the data of multiple tables. The statement below does not show students don't have a teacher, due to the nature of INNER JOIN.

```sh
SELECT 
    Student.StudentID, 
    Student.StudentName, 
    Teacher.TeacherID, 
    Teacher.TeacherName
FROM Student
INNER JOIN Teacher ON Student.TeacherID = Teacher.TeacherID;
```
<br/>

The statement below is similar to the one above. However, this statement prints all students, even if they have no assigned teacher.

```sh
SELECT 
    Student.StudentID, 
    Student.StudentName, 
    Teacher.TeacherID, 
    Teacher.TeacherName
FROM Student
LEFT JOIN Teacher ON Student.TeacherID = Teacher.TeacherID;
```

<br/>

</details>
