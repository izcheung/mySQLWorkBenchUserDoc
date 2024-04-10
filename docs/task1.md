# Manage a TABLE

## Overview
SQL is the most commonly used programming language when managing relational database. In relational databases, all data are organized into tables, which are structured collections of rows and columns. Therefore, it is important to first learn the basis of how to manage relational databases, which includes tasks such as creating, inserting, deleting, and dropping tables.

## Set up a database
Before getting started, we will need to create a database to store tables.

1. Open a new query tab under 'File' and then click on 'New Query Tab'.

1. To create a new database, input the following code in the query window and execute it:

    ``` sql
    CREATE DATABASE <DatabaseName>;    
    ```

2. Click the refresh button to see your database appear on the schema pane. 

    !!! success
        ![Image title](./images/DatabaseName4.jpg){ align=left }


3. After creating the database, make sure you select that database and use it. 
``` sql
USE <DatabaseName>;
```

    > You should see a green checkmark in the action output to signify that the command successfully ran.

## Create a table
Once you have created a database, you can create and put a new table inside the database. 

1. Run the command below to create a table.
``` sql
CREATE TABLE <TableName>        
(<ColumnName> DATATYPE,         
 <ColumnName> DATATYPE,         
 <ColumnName> DATATYPE, ...);
```

2. Click the refresh button to see your table under the database in the Schema pane.


    > At this point, you should see the new table.

    !!! success
        ![CreateTable](images/CreateTable.jpg)

## Insert a tuple into a table
After creating a table, you can populate the table with data.

1. To insert a tuple into a table, use the following command:
``` sql
INSERT INTO <TableName> (<ColumnName1>, <ColumnName2>, <ColumnName3>, ...) 
VALUES (<Value1>, <Value2>, <Value3>, ...); 
```

    > The ```INSERT INTO``` command is used to specify the name of the table you are inserting into. ```VALUES``` specifies the list of values that corresponding to the respective columns listed above.

    !!! note
        Ensure that the values you are inserting into the columns are of the correct datatype.


2. Verify that the insertion was made correctly by running the following command.  We will refer to this step many times for verifying that the correct changes have been made. You should see the new row in the table.

    ``` sql
    SELECT * FROM <TableName>;
    ```

    > The ```SELECT``` command chooses which columns to include in the returned table. The ```*``` symbol means to include all records. The ```FROM``` command tells SQL which table to query from.

    !!! success
        ![Image title](images/VerifyTable.jpg)

## Update a table record
1. In the scenario that you wish to make a change to a record, you can run the following command:
``` sql
UPDATE <TableName>
SET <ColumnName> = <New Value>, ...
WHERE <ColumnName> = <Value>;
```
    The ```UPDATE``` keyword indicates that you would like to make changes to an existing table. The ```SET``` keyword specifies which column you wish to change. The ```WHERE``` keyword is used to extract only the records that fulfill the specified condition.

    !!!note
        If you encounter an error Error code 1175, disable safe update mode by referring to the troubleshoot guide.

2. Verify that the correct update was made by running the same command in [step 2](task1.md#insert-a-tuple-into-a-table) of 'Insert a tuple into a table'. You should see the new changes in the updated table.

    !!! success
        ![Update Table Record](images/UpdateTable.jpg)

## Delete a table record

1. In order to delete a table record, run the following command.
``` sql
DELETE FROM <TableName>
WHERE <condition>;
```
    > The ```DELETE FROM``` keyword specifies which table you would like to delete records from. The ```WHERE``` clause specifies the conditions that must be met before the record is deleted.

    !!! warning
        If you use the DELETE FROM clause without using in junction with the WHERE clause, all the rows in the table will be deleted.

2. Verify the correct deletion was made by running the same command in [step 2](task1.md#insert-a-tuple-into-a-table) of 'Insert a tuple into a table'. You should see that the record has been deleted. 


    !!! success
        ![Delete Table Record](images/DeleteTableData.jpg)



## Drop a SQL table
Finally, We will go over how to drop an entire SQL table. 

1. Run the following command to drop an entire table.
``` sql
DROP TABLE <TableName>;
```
    The ```DROP TABLE``` keyword specifies which table you would like to drop.

    !!! success
        ![Drop Table](images/DropTable.jpg)


## Conclusion
By the end of this section, you will have learned the SQL commands for the following:

- [x] Understanding what SQL is and how its applied
- [x] Setting up a database
- [x] Creating a SQL table
- [x] Inserting a tuple into a table
- [x] Updating a table record
- [x] Deleting a table record
- [x] Dropping SQL table


in my sql workbench, open up a new query tab to input ...

After every query, run the steps
Create table section - redo screenshot to show columns
No bullet points
Explain log table and purpose of it.
What the command 