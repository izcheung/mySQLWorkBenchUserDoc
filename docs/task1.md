# How to create, manipulate, and drop a SQL table



## Overview
SQL is by far the most commonly used programming language when managing relational database. In relational databases, all data are organized into tables, which are structured collections of rows and columns. Therefore, it is important to first learn the basis of how to manage relational databases including how to create, manipulate, and drop tables. 

## Setting up a database
Before getting started, we will need to create a database where the table can be saved in.

1. Create a new database by entering the following code in the query window and then click the (lightningbolt) icon to run. 
```
CREATE <DatabaseName>;      // Replace <DatabaseName> with name of database
```

2. After creating the database, make sure you choose that database to use it.
```
USE <DatabaseName>;     // Replace <DatabaseName> with name of database
```

At this point, a database should be made 

## How to create a SQL table
After you have created a database, you will need to create a table to put it inside the database. 

3. Type the command below to create a table.
```
CREATE TABLE <TableName>        // Replace <TableName> with the name of table
(<ColumnName> DATATYPE,         // Replace the <ColumnName> with the name of your columns and DATATYPE with the appropriate datatype
 <ColumnName> DATATYPE,         
 <ColumnName> DATATYPE);
```

The ```CREATE``` keyword creates a new table
!!! note

    Set as many ColumnNames as needed to make your desired table.

4. Verify that the correct table was made by running the following command. 
```
SELECT * FROM <TableName>
```
The ```SELECT``` command chooses which columns to include in the returned table. The ```*``` symbol means to include all records. The ```FROM``` command tells SQL which table to query from.

At this point, you should see that a new table is made - graphics.


## How to update a table record
5. In order to update a table record, run the following command.
```
UPDATE <TableName>
SET <ColumnName> = Value, <ColumnName> = Value, ... // Replace 'Value' with your desired value.  
```
The ```UPDATE``` keyword indicates that you would like to make changes to an existing table.
The ```SET``` keyword specifies which column you wish to change.

6. Verify that the correct update was made by running the same command in step 4. You should see the new changes in the updated table.

## How to delete a table record
7. In order to delete a table record, run the following command.

```
DELETE FROM <TableName>
WHERE condition
```
The ```DELETE FROM``` keyword specifies which table you would like to delete records from.
The ```WHERE``` clause specifies the conditions that must be met before the record is deleted.

!!! warning
Warning: If you use the DELETE FROM clause without using in junction with the WHERE clause, all the rows in the table will be deleted.

8. Verify the correct deletion was made by running the same command in step 4. You should see that the record has been deleted.

## How to drop SQL tables
Finally, We will go over how to drop an entire SQL table. 
9. Run the following command to drop an entire table.

```
DROP TABLE <TableName>;
```
```DROP TABLE``` is used to specify which table to delete.


## Conclusion
By the end of this section, you will have learned the queries for the following:
- Setting up a database
- How to create a SQL table
- How to update a table record
- How to delete a table record
- How to drop SQL tables


