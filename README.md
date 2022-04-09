Installation on Ubuntu:-

1) Go to terminal and type command:- sudo apt-get install mysql-server
2) To start mysql :- sudo /etc/init.d/mysql start
     To restart mysql:- sudo /etc/init.d/mysql restart
     To stop mysql :- sudo /etc/init.d/mysql stop


     or 

     sudo start mysql  	and  sudo stop mysql  will also work.

----------------------------------------------------------------------------------------------------------------------------

Getting the mysql command line (ubuntu):-

First start the mysql server.
Then in  terminal give the command :-  mysql -u root -h localhost -p

 Now we have the mysql command line . Now database tasks can be performed from here.

----------------------------------------------------------------------------------------------------------------------------

Creating the Database:-

create database database_name;

This syntax will create a database with name ‘database_name‘  that will hold all the tables, procedures , triggers, views etc that are specified to be in ‘database_name’.

----------------------------------------------------------------------------------------------------------------------------

Data types:-

Numeric Types	

TINYINT  - A very small integer
SMALLINT - A small integer
MEDIUMINT - A medium-sized integer
INT - A standard integer
BIGINT - A large integer
DECIMAL - A fixed-point number
FLOAT - A single-precision floating-point number
DOUBLE - A double-precision floating-point number
BIT - A bit field



String Types

CHAR - A fixed-length non-binary (character) string
VARCHAR - A variable-length non-binary string
BINARY - A fixed-length binary string
VARBINARY - A variable-length binary string
TINYBLOB - A very small BLOB (binary large object)
BLOB - A small BLOB
MEDIUMBLOB - A medium-sized BLOB
LONGBLOB - A large BLOB
TINYTEXT - A very small non-binary string
TEXT - A small non-binary string
MEDIUMTEXT - A medium-sized non-binary string
LONGTEXT - A large non-binary string
ENUM - An enumeration; each column value may be assigned one enumeration member
SET - A set; each column value may be assigned zero or more set members


Date and Time Types

DATE - A date value in 'CCYY-MM-DD' format
TIME - A time value in 'hh:mm:ss' format
DATETIME - A date and time value in 'CCYY-MM-DD hh:mm:ss' format
TIMESTAMP - A timestamp value in 'CCYY-MM-DD hh:mm:ss' format
YEAR - A year value in CCYY or YY format


----------------------------------------------------------------------------------------------------------------------------
Creating Tables:-

The CREATE TABLE statement is used to create a table in a database.

CREATE TABLE table_name
(
column_name1 data_type,
column_name2 data_type,
column_name3 data_type,
....
)


Now we want to create a table called "Persons" that contains five columns: P_Id, LastName, FirstName, Address, and City.

CREATE TABLE Persons
(
P_Id int,
LastName varchar(255),
FirstName varchar(255),
Address varchar(255),
City varchar(255)
)

------------------------------------------------------------------------------

Select statement:-

The SELECT statement is used to select data from a database.
The result is stored in a result table, called the result-set.

SELECT column_name(s)
FROM table_name

or

Select * from table_name will display all the rows from the table_name table.

Now we want to select the content of the columns named "LastName" and "FirstName" from the table above.
We use the following SELECT statement:

SELECT LastName,FirstName FROM Persons


------------------------------------------------------------------------------

The INSERT INTO Statement


INSERT INTO table_name
VALUES (value1, value2, value3,...) is used to insert a new row in a table.

--------------------------------------------------------------------------------------------------------


The UPDATE Statement

UPDATE table_name
SET column1=value, column2=value2,...
WHERE some_column=some_value


is used to update existing records in a table.


----------------------------------------------------------------------------------------------------------------------------

The DELETE Statement
The DELETE statement is used to delete rows in a table.


DELETE FROM table_name
WHERE some_column=some_value

------------------------------------------------------------------------------

The WHERE Clause 

The WHERE clause is used to extract only those records that fulfill a specified criterion.




We use the following SELECT statement:
SELECT * FROM Persons WHERE City='Sandnes'


----------------------------------------------------------------------------------------------------------------------------


The ORDER BY Keyword


The ORDER BY keyword is used to sort the result-set by a specified column.
The ORDER BY keyword sort the records in ascending order by default.
If you want to sort the records in a descending order, you can use the DESC keyword.


SELECT column_name(s)
FROM table_name
ORDER BY column_name(s) ASC|DESC

------------------------------------------------------------------------------
Primary Key and foreign key

The PRIMARY KEY constraint uniquely identifies each record in a database table.
Primary keys must contain unique values.
A primary key column cannot contain NULL values.
Each table should have a primary key, and each table can have only ONE primary key.



CREATE TABLE Persons
(
P_Id int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
PRIMARY KEY (P_Id)//primary key
)


A FOREIGN KEY in one table points to a PRIMARY KEY in another table.
Let's illustrate the foreign key with an example. Look at the following two tables:

CREATE TABLE Orders
(
O_Id int NOT NULL,
OrderNo int NOT NULL,
P_Id int,
PRIMARY KEY (O_Id),
FOREIGN KEY (P_Id) REFERENCES Persons(P_Id)
)


Note that the "P_Id" column in the "Orders" table points to the "P_Id" column in the "Persons" table.
The "P_Id" column in the "Persons" table is the PRIMARY KEY in the "Persons" table.
The "P_Id" column in the "Orders" table is a FOREIGN KEY in the "Orders" table.
The FOREIGN KEY constraint is used to prevent actions that would destroy links between tables.
The FOREIGN KEY constraint also prevents that invalid data form being inserted into the foreign key column, because it has to be one of the values contained in the table it points to.


-----------------------------------------------------------------------------------------------------------------------



SQL JOIN

The JOIN keyword is used in an SQL statement to query data from two or more tables, based on a relationship between certain columns in these tables.


INNER JOIN: Return rows when there is at least one match in both tables.
LEFT JOIN: Return all rows from the left table, even if there are no matches in the right table.
RIGHT JOIN: Return all rows from the right table, even if there are no matches in the left table.
FULL JOIN: Return rows when there is a match in one of the tables.


SQL INNER JOIN Keyword

The INNER JOIN keyword return rows when there is at least one match in both tables.


SELECT column_name(s)
FROM table_name1
INNER JOIN table_name2
ON table_name1.column_name=table_name2.column_name


SQL LEFT JOIN Keyword
The LEFT JOIN keyword returns all rows from the left table (table_name1), even if there are no matches in the right table (table_name2).


SELECT column_name(s)
FROM table_name1
LEFT JOIN table_name2
ON table_name1.column_name=table_name2.column_name


SQL RIGHT JOIN Keyword


The RIGHT JOIN keyword returns all the rows from the right table (table_name2), even if there are no matches in the left table (table_name1).
SELECT column_name(s)
FROM table_name1
RIGHT JOIN table_name2
ON table_name1.column_name=table_name2.column_name

SQL FULL JOIN Keyword
The FULL JOIN keyword return rows when there is a match in one of the tables.

SELECT column_name(s)
FROM table_name1
FULL JOIN table_name2
ON table_name1.column_name=table_name2.column_name


------------------------------------------------------------------------------

Index
An index can be created in a table to find data more quickly and efficiently.
The users cannot see the indexes, they are just used to speed up searches/queries.


Updating a table with indexes takes more time than updating a table without (because the indexes also need an update). So you should only create indexes on columns (and tables) that will be frequently searched against.

Indexes can be unique which does not allow the duplication.

CREATE INDEX index_name
ON table_name (column_name)

The SQL statement below creates an index named "PIndex" on the "LastName" column in the "Persons" table:

CREATE INDEX PIndex
ON Persons (LastName)

------------------------------------------------------------------------------


SQL Functions:-


SQL Aggregate Functions:-

AVG() - Returns the average value
COUNT() - Returns the number of rows
FIRST() - Returns the first value
LAST() - Returns the last value
MAX() - Returns the largest value
MIN() - Returns the smallest value
SUM() - Returns the sum



SQL Scalar functions:-


UCASE() - Converts a field to upper case
LCASE() - Converts a field to lower case
MID() - Extract characters from a text field
LEN() - Returns the length of a text field
ROUND() - Rounds a numeric field to the number of decimals specified
NOW() - Returns the current system date and time
FORMAT() - Formats how a field is to be displayed



----------------------------------------------------------------------------------------------------------------------------

SubQueries:-




The subquery is enclosed in parentheses, but otherwise it has the familiar form of a SELECT statement, with a FROM clause and optional WHERE, GROUP BY, HAVING, and ORDER BY clauses. The form of these clauses in a subquery is identical to that in a SELECT statement, and they perform their normal functions when used within a subquery. There are, however, a few differences between a subquery and an actual SELECT statement: 

 In the most common uses, a subquery must produce a single column of data as its
query results. This means that a subquery almost always has a single select item in
its SELECT clause.

• While the ORDER BY clause can be specified in a subquery, it is rarely used there.
The subquery results are used internally by the main query and are never visible 
to the user, so it makes little sense to sort them. Moreover, sorting large numbers of
rows can adversely affect performance.

• Column names appearing in a subquery may refer to columns of tables in the main
query.
• In most implementations, a subquery cannot be the UNION of several different
SELECT statements; only a single SELECT is allowed.


SELECT CITY
FROM OFFICES
WHERE TARGET > (SELECT SUM(QUOTA)
FROM SALESREPS
WHERE REP_OFFICE = OFFICE);


from the above statement we can see that main query uses the result of other query for its completion. Here the other query is the subquery.



----------------------------------------------------------------------------------------------------------------------------


Stored procedure:-

A stored procedure, by definition, is a segment of declarative SQL code which is stored in the database catalog and can be invoked later by a program, a trigger or even a stored procedure.

Its more like a function or method in other programming languages.



DELIMITER //
CREATE PROCEDURE procedure_name()
  BEGIN
  SELECT *  FROM table_name;
  END //
DELIMITER;

Delimiter changes the delimit character for procedures and triggers.


Calling the stored procedure

sql> call procedure_name();


We can also have conditional control and loops in the procedures and triggers.

Conditional control enables you to execute the code based on the value of an expression or a combination of expression using logical operators.


IF expression THEN commands
   [ELSEIF expression THEN commands]
   [ELSE commands]
   END IF;

and

When multiple conditions are used with IF statement the code is not easy to read. At this time, the CASE can be used to make the code clearer.



CASE 
   WHEN expression THEN commands
   …
   WHEN expression THEN commands
   ELSE commands
   END CASE;



LOOPS in procedure and trigger:-

MySQL stored programming language supports loop which allows you to process commands iteratively.

WHILE expression DO
   Statements
END WHILE


----------------------------------------------------------------------------------------------------------------------------

Trigger.

SQL trigger is an SQL statements or a set of SQL statements which is stored to be activated or fired when an event associating with a database table occurs. The event can be any event including INSERT, UPDATE  and DELETE.

The difference between a trigger and a stored procedure is that a trigger is activated or called when an event happens in a database table, a stored procedure must be called explicitly. 

In the sample database, we have table employees as follows:



CREATE TABLE `employees` (
  `employeeNumber` int(11) NOT NULL,
  `lastName` varchar(50) NOT NULL,
  `firstName` varchar(50) NOT NULL,
  `extension` varchar(10) NOT NULL,
  `email` varchar(100) NOT NULL,
  `officeCode` varchar(10) NOT NULL,
  `reportsTo` int(11) default NULL,
  `jobTitle` varchar(50) NOT NULL,
  PRIMARY KEY  (`employeeNumber`)
)

Now you want to keep the changes of employee's data in another table whenever data of an employee's record changed. In order to do so you create a new table called employees_audit  to keep track the changes.

CREATE TABLE employees_audit ( 
id int(11) NOT NULL AUTO_INCREMENT, 
employeeNumber int(11) NOT NULL, 
lastname varchar(50) NOT NULL, 

changedon datetime DEFAULT NULL, 
action varchar(50) DEFAULT NULL, 
PRIMARY KEY (id) 
)
In order to keep track the changes of last name of employee we can create a trigger that is fired before we make any update on the employees table.


DELIMITER $$
CREATE TRIGGER before_employee_update 
BEFORE UPDATE ON employees
FOR EACH ROW BEGIN
INSERT INTO employees_audit
SET action = 'update',
employeeNumber = OLD.employeeNumber,
lastname = OLD.lastname,
changedon = NOW(); END$$
DELIMITER ;

You can test the trigger which created by updating last name of any employee in employees table. Suppose we update last name of employee which has employee number is 3:

UPDATE employees
SET lastName = 'Phan'
WHERE employeeNumber = 1056

After this operation trigger is executed.

----------------------------------------------------------------------------------------------------------------------------





Cursor:-

MySQL supports cursor in stored procedures, functions and triggers. Cursor is used to iterate through a set of rows, which returned by a query, and process individual row.


Read only: it means you cannot update the cursor.
Non-scrollable: it only can traverse in one direction and cannot skip, move back or forth in result set.
Asensitive: you should avoid update table while open a cursor on that table otherwise you may get unexpected results.


First you have to declare a cursor using DECLARE statement:

DECLARE cursor_name CURSOR FOR SELECT_statement;

Second you have to open the cursor using OPEN statement. You must open cursor before fetching rows from it.

OPEN cursor_name;

Next you can retrieve next row from cursor and move the cursor to the following row in a result set by using FETCH statement.

FETCH cursor_name INTO variable list;

And finally, you must close the cursor to deactivate it and release the memory associated with that cursor. To close the cursor you use CLOSE statement:

CLOSE cursor_name;

One of the most important point when working with cursor is you should use a NOT FOUND handler to avoid raising a fatal “no data to fetch” condition. 

----------------------------------------------------------------------------------------------------------------------------



 VIEW Statement

In SQL, a view is a virtual table based on the result-set of an SQL statement.

A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.

You can add mySQL functions, WHERE, and JOIN statements to a view and present the data as if the data were coming from one single table.


CREATE VIEW view_name AS
SELECT column_name(s)
FROM table_name
WHERE condition

A view always shows up-to-date data! The database engine recreates the data, using the view's SQL statement, every time a user queries a view.

You can delete a view with the DROP VIEW command.

DROP VIEW view_name





For Advanced mysql statements and elaborated mysql function wisit to:- www.w3schools.com/sql/sql_view.asp


References:-

http://www.mysqltutorial.org/

http://dev.mysql.com/

http://www.w3schools.com/sql/sql_top.asp

http://www.roseindia.net/mysql/mysql5/triggers.shtml
