MySQL cheat cheat / Syntax Guide 
1. How to log into MySQL from terminal

- Firstly SSH into your A2 Hosting site. 
- Then run this command mysql -u root - p
- MySQL will then prompt you for a password after you hit enter.

2. How to Show users 
- Once successfully logged into mySQL
- run this command to show all users 
- SELECT user FROM mysql.user;
- *Important to note to use a semi colon (;) at the end of each command to inform MySQL that its the end of the statement*

3. How to create Users
- Inside MySQL run this command 
- CREATE USER 'username' IDENTIFIED BY 'password';
- Replace username and password with the username and password of your choice

Alternatively you are able to set up a user by simply specifying the machine hosting the database. 

- If you are working on the machine with MySQL, use username@localhost to define the user.
- If you are connecting remotely, use username@ip_address, and replace ip_address with the actual address of the remote system hosting MySQL.
- The command will then be 

- CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
- or CREATE USER 'username'@'ip_address' IDENTIFIED BY 'password';

You are also able to create a yser that is able to connect from any machine with the following command 

- CREATE USER 'username'@'%' IDENTIFIED BY 'password';

4. How to GRANT PRIVILEGES, Show granted privileges and remove.

- The standard syntax to used to grant privileges to a user account is 

- GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';
- To show granted privileges 
- SHOW GRANTS FOR 'username'; 

If you wanted to revoke privileges to a user run this command 
- REVOKE permission_type ON database.table TO 'username'@'localhost';

5. How to SHOW, DELETE & CREATE DATABASES & SELECT DATABASES

- If you wish to see all databases run this command in mysql 
- show databases; 
- If you wish to delete a database run this command 
- DROP DATABASE 'database name';
- If you wish to Select a Database, firstly run the SHOW DATABASES; command. Then run this command
- USE 'DATABASENAME';

6. How to CREATE a TABLE with Columns and their data types

- MySQL stores all data in tables, each MySQL database table consists of rows and columns. The columns specify the type of data where as the rows contain the actual data itself. 
- Creating a table in MySQL looks something like this

CREATE TABLE 'table name' (
column_name data_type CONSTRAINT,
column_name data_type CONSTRAINT,
column_name data_type CONSTRAINT,
);

- Data Types in MySQL consists of

INT - Used to store numeric values in the range of -2147483648 to 2147483647
DECIMAL  - Stores decimal values with exact precision 
CHAR - Stores a fixed length strings with a maximum size of 255 characters 
VARCHAR - Used to store variable-length strings with a maximum size of 65,535 characters
when using varchar you can set the limit of characters in parenthesis after declaring the data_type 
varchar(200)
TEXT - Used to also store strings with a maximum size of 65,535 characters
DATE - Stores data values in the YY-MM-DD format 
DATETIME - Used to store combined date/time values in the YY-MM-DD HH:MM:SS format. 
TIMESTAMP - Stores timestamp values. TIMESTAMP values are stored as the number of seconds since the Unix epoch



- Constraints in MySQL 
The constraint in MySQL is used to specify the rule that allows or restricts what values/data will be stored in the table. Providing a suitable method to ensure data accuracy and integrity inside the table. Also helping to limit the type of data that will be inserted inside the table. If any interruption occurs between the constraint and the data action, the action will fail. 

Constraints in MySQL fall under two types 

1. Column Level Constraints: These constraints are applied only to the single column that limits the type of particular column data.

2. Table Level Constraints: These constraints are applied to the entire table that limits the type of data for the whole table.

The following are the most commonly used constraints in MySQL. 

- NOT NULL - Specifies that the column cannot have NULL or empty values. 

- UNIQUE - Ensures that all data values inserted into the column will be unique. Preventing duplicates. 

- CHECK - Determines whether the value associated with the column is valid or not with the given 
condition.

- DEFAULT - his constraint is used to set the default value for the particular column where we have not specified any value. It means the column must contain a value, including NULL.

- PRIMARY KEY - This constraint is used to identify each record in a table uniquely, if the column contains a primary key constraint then it cannot be null or empty. There must be only one primary key per table. 

- AUTO_INCREMENT - Automatically generates a unique number whenever we insert a new record into the table. Generally used for the primary key constraint. 

- UNIQUE - The UNIQUE constraint restricts one or more columns to contain unique values within a table.

- INDEX - This constraint allows us to create and retrieve values from the table very quickly and easily. An index can be created using one or more than one column

- FOREIGN KEY - This constraint is used to link two tables together. It is also known as the referencing key. A foreign key column matches the primary key field of another table. It means a foreign key field in one table refers to the primary key field of another table.


7. How to SHOW, DELETE & DROP Tables
- If you wish to drop a table run this command 
- drop 'table name';
- If you wish to show tables run this command 
- SHOW TABLES; 
- if you wish to delete a table, run this command
- drop table 'table name';

8. How to Insert ROWS & RECORDS (single and multiple) 
Multiple Insertion 
First, specify the name of table that you want to insert after the INSERT INTO keywords.

Second, specify a comma-separated column list inside parentheses after the table name.

Third, specify a comma-separated list of row data in the VALUES clause. Each element of the list represents a row. The number of values in each element must be the same as the number of columns in the column_list.

INSERT INTO table_name (column_list) Values (value_list_1), (value_list_2);

Single Insertion 

INSERT INTO table_name (column_list) VALUES (value_1, value_2);
 
Keep in mind that you must list of the columns in the order they are displayed in the table. The same goes for the values. 

9. How to SELECT with the WHERE Clause

- The WHERE clause works like an if condition in any programming language. This clause is used to compare the given value with the field value available in a MySQL table. If the given value from outside is equal to the available field value in the MySQL table, then it returns that row. 

- SELECT Name District, Population from city where District = 'New York';

In the example above, I Selected the name district and population from a world database, from a city table WHERE the district = 'New York';

10. How to SELECT with the WHERE Clause using a range

- MySQL kindly offers the  IN and BETWEEN clause that you can use in conjunction with the WHERE clause.
- MySQL also offers the AND clause. 

- Example command 

- SELECT * FROM table_name WHERE salary  BETWEEN 4000 AND 9000; 
- that will give you the salaries between 4000 and 9000. 

- You can build conditions that will search for a range of strings 
SELECT * FROM table_name WHERE customer_name BETWEEN 'E' AND 'J'; 
- that will give you all the employee names between 'E' and 'J'


11. How to DELETE an individual ROW
- If you wish to delete an individual row from a table run this command. 
- DELETE FROM table_name WHERE [Condition]; 

- DELETE FROM table_name tells MySQL server to remove rows from the table. 

- [WHERE condition] is optional and is used to put a filter that restricts the number of rows affected by the DELETE syntax MySQL row query.

12. How to UPDATE a ROW 
- In MySQL you can update a single row of your choice, run the following commands and tailor it to your database requirements. 

- It is the WHERE clause that will determine how many records will be updated. 

- UPDATE table_name SET column_name = 'Its new value' WHERE "column_name" = 'Its new value';


12. How to add a new column and modify it 

- To add a new column to an existing table you will run this command. 
- ALTER TABLE 'table_name' ADD [COLUMN] column_name column_definition


13. How to Order by and use Distinct
Order By
- The order by clause is used to sort data returned by a query in either ascending or descending order. The basic syntax used to run this clause can look something like this. 
-   SELECT column_list FROM table_name ORDER BY column_name asc; 

Distinct 
- The select distinct statement is used to return only distinct (different) values. Inside a table, a column often contains many duplicate values, sometimes you only want to list the different (distinct) values. The command looks something like this 
- SELECT DISTINCT column_name FROM table_name; 


14. How to Concatenate Columns
- The solution to concatenate columns in MySQL SELECT statements, you can concatenate columns using MySQL's Concat() function. The query will look like this. 
- SELECT  column_name CONCAT(column_name1, " ", column_name2, " ", column_name3) AS existing_column
FROM table_name;

15. How to Select Distinct Rows
If you wish to select a distinct Row run this command and fit it to your database needs! 
- SELECT DISTINCT (column_name) FROM table_name;

16. How to use LIKE to Search
The LIKE Operator is used in a WHERE clause to search for a specified pattern in a column. There is two wildcards often used in conjunction with the LIKE operator. 

- The percent sign (%) represents zero, one, or multiple characters.
- The underscore sign (_) represents one, single character 

- WHERE CustomerName LIKE 'a%' Finds any values that start with "a"
- WHERE CustomerName LIKE '%a' Finds any values that end with "a"
- WHERE CustomerName LIKE '%or%' Finds any values that have "or" in any position
- WHERE CustomerName LIKE '_r%  Finds any values that have "r" in the second position
- WHERE CustomerName LIKE 'a_%   Finds any values that start with "a" and are at least 2 characters in length
- WHERE CustomerName LIKE 'a__%' Finds any values that start with "a" and are at least 3 characters in length
- WHERE ContactName LIKE 'a%o' Finds any values that start with "a" and ends with "o"



- The Syntax will look like 
- SELECT column_name, column_name FROM table_name WHERE column_name LIKE pattern 

Lets say we have a table called books, and we are trying to access all the book titles that begin with 'A'
this is what that would look like. 
- SELECT Title FROM Books WHERE Title LIKE "%A"; 

17. How Select using IN
The IN operator is used to check whether a particular value exists within a set of values or not. Its standard syntax looks something like this. 
- SELECT column_list FROM table_name WHERE column_name IN (value1, value2); 


18. How to Create & Remove Index
- To create indexes use the CREATE INDEX COMMAND 
- CREATE INDEX index_name ON table_name (column_name);

- To remove an index 
- DROP INDEX index_name ON table_name;

19. Create Two Tables demonstrating a one to many relationship that shows a PK & FK

CREATE TABLE Orders (
OrderID INT NOT NULL, 
OrderNumber INT NOT NULL, 
PersonID int, 
PRIMARY KEY (OrderID),
FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);



CREATE TABLE Persons (
PersonID int, 
LastName varchar(50),
FirstName varchar(50),
Age int,
PRIMARY KEY (PersonID)
);

20. How to use Inner Join
- The inner join is used to returns only those results from the tables that match the specified condition and hides the other rows and columns. MySQL assumes it as a default join, so it is optional to use the Inner Join keyword with the query. The Inner Join keyword is used with the SELECT statement. 

I will create two tables to make this example more clearly. 

CREATE TABLE student (
    student_id int, 
    stud_fname varchar(200),
    stud_lname varchar(200),
    city varchar(200),
);

CREATE TABLE technologies (
    student_id int,
    tech_id int, 
    inst_name varchar(200),
    technology varchar(200)
);

- To select records from both of the tables i will execute the following query

- SELECT students.stud_fname, students.stud_lname, students.city, technologies.technology
FROM students INNER JOIN technologies ON students.student_id = technologies.tech_id;


21. How to JOIN Multiple Tables 
- The standard syntax for joining multiple tables looks something similar to this. 

SELECT table_one.column_one, table_three.column_one
FROM table_one 
JOIN table_two ON table_one.primarykey = table_two.foreignkey
JOIN table_three ON table_two.primarykey = table_three.foreignkey 

- Firstly we Join table 1 and table two which produces a temporary table with a combination of data from table 1 and table 2, which is then joined to table 3. This formula can be extended to more than 3 tables. 
