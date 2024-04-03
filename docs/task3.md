# How to create and drop triggers

## Overview
Triggers are special types of stored procedures that automatically execute or fire in response to certain events on a table or view in a database. Understanding how to create and manage triggers is essential for implementing complex business logic directly on the database level, ensuring data integrity, and automating tasks such as auditing changes, enforcing constraints, or updating related tables. This section provides a step-by-step guide on how to create and drop triggers, empowering you to enhance the functionality and efficiency of your database management.


## Setting up tables
Before you create a trigger, it's important to set up your tables properly.

1. Follow instructions in [How to create, manipulate, and drop a SQL table](task1.md){:target="_blank"} to create some tables and insert some data.


2. Verify that the correct table was made by running the following command for all the tables created in step 1. 
    ```
    SELECT * FROM <TableName>;
    ```
    The ```SELECT``` command chooses which columns to include in the returned table. The ```*``` symbol means to include all records. The ```FROM``` command tells SQL which table to query from.

    At this point, you should see that a new table is made 
    ![Image title](https://dummyimage.com/600x400/eee/aaa)

## How to create a trigger
Creating a trigger involves specifying the timing (`BEFORE` or `AFTER` the event), the event (`INSERT`, `UPDATE`, or `DELETE`) that triggers it, and the operations to be performed.

### Create a BEFORE INSERT trigger
1. Execute the command below to create a trigger:
    ```
    CREATE TRIGGER <TriggerName>
    BEFORE INSERT ON <TableName>
    FOR EACH ROW
    BEGIN
        -- Trigger logic goes here
    END;
    ```

    An example of trigger logic could be:
    ```
    SET NEW.<ColumnName> = LOWER(NEW.<ColumnName>);
    ```

2. Examine the trigger by performing the action it's designed to respond to on the specified table.

    For example, after setting up a `BEFORE INSERT` trigger to convert a column's data to lowercase *before insertion*, you can test the trigger's functionality by attempting to insert a record into the designated table, deliberately using uppercase letters in the targeted column. Execute the following command to observe the trigger in action:
    ```
    INSERT INTO <TableName> (<ColumnName>, ...)
    VALUES ('UPPERCASE DATA', ...);
    ```

3. Verify that the correct data has been inserted by running the following command for the table updated in step 2. 
    ```
    SELECT * FROM <TableName>;
    ```

    This step verifies that the `BEFORE INSERT` trigger is applied to new values.

### Create a AFTER INSERT trigger
1. Execute the command below to create a trigger:
    ```
    CREATE TRIGGER <TriggerName>
    AFTER INSERT ON <TableName>
    FOR EACH ROW
    BEGIN
        -- Trigger logic goes here
    END;
    ```

    An example of trigger logic could be:
    ```
    INSERT INTO <LogTableName> (<ForeignKeyColumn>, <TimestampColumn>)
    VALUES (NEW.<ForeignKeyValue>, NOW());
    ```
    !!! note
        For this example, ensure you have created a log table named `<LogTableName>` alongside your main table `<TableName>`. For guidance on creating a new table, please refer to [How to create, manipulate, and drop a SQL table](task1.md){:target="_blank"}.

2. Examine the trigger by performing the action it's designed to respond to on the specified table.

    For example, after setting up a `AFTER INSERT` trigger to log a record in the log table *after insertion*, you can test the trigger's functionality by attempting to insert a record into the designated table and note the change in the log table. Execute the following command to observe the trigger in action:
    ```
    INSERT INTO <TableName> (<ColumnName>, ...)
    VALUES ('anything', ...);
    ```

3. Verify that a log record has been created successfully by running the following command for the log table. 
    ```
    SELECT * FROM <LogTableName>;
    ```

    This step verifies that the trigger is applied to the `AFTER INSERT` event.

## How to drop triggers
Finally, We will go over how to drop the trigger. 

1. Run the following command to drop the trigger in database.
    ```
    DROP TRIGGER [IF EXISTS] <TriggerName>;
    ```

2. Repeat step 2 and 3 from `Create a BEFORE INSERT trigger` or `Create a AFTER INSERT trigger` to verify if trigger has been dropped.



## Conclusion
By the end of this section, you have gained knowledge on the following tasks:

- [x] The purpose and functionality of triggers in a database
- [x] How to create and examine BEFORE INSERT triggers
- [x] How to create and examine AFTER INSERT triggers
- [x] How to drop triggers in database
