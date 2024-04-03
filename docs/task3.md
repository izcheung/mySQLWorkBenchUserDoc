# Create and drop triggers

## Overview
Triggers are special types of stored procedures that automatically executes or fires in response to certain events on a table or view in a database. Understanding how to create and manage triggers is essential for implementing complex business logic directly on the database level to ensure data integrity. It is also used to automate tasks such as auditing changes, enforcing constraints, or updating related tables. 


## Set up tables
Before you create a trigger, it is important to set up your tables properly.

1. Follow instructions in [Create a TABLE](task1.md#create-a-table){:target="_blank"} to create some tables and insert data into them.


## How to create a trigger
Creating a trigger involves specifying the timing (`BEFORE` or `AFTER` the event), the event (`INSERT`, `UPDATE`, or `DELETE`) that triggers it, and the operations to be performed.

### BEFORE INSERT trigger
1. Execute the command below to create a trigger:
    ``` sql
    CREATE TRIGGER <TriggerName>
    BEFORE INSERT ON <TableName>
    FOR EACH ROW
    BEGIN
        -- Trigger logic goes here
    END;
    ```

    An example of trigger logic could be:
    ``` sql
    SET NEW.<ColumnName> = LOWER(NEW.<ColumnName>);
    ```

2. Examine the trigger by performing the action it's designed to respond to on the specified table.

    For example, after setting up a `BEFORE INSERT` trigger to convert a column's data to lowercase *before insertion*, you can test the trigger's functionality by attempting to insert a record into the designated table, deliberately using uppercase letters in the targeted column. Execute the following command to observe the trigger in action:
    ``` sql
    INSERT INTO <TableName> (<ColumnName>, ...)
    VALUES ('UPPERCASE DATA', ...);
    ```

3. Verify that the correct data has been inserted by running the following command for the table updated in step 2. 
    ``` sql
    SELECT * FROM <TableName>;
    ```

    This step verifies that the `BEFORE INSERT` trigger is applied to new values.

### AFTER INSERT trigger
1. Execute the command below to create a trigger:
    ``` sql
    CREATE TRIGGER <TriggerName>
    AFTER INSERT ON <TableName>
    FOR EACH ROW
    BEGIN
        -- Trigger logic goes here
    END;
    ```

    An example of trigger logic could be:
    ``` sql
    INSERT INTO <LogTableName> (<ForeignKeyColumn>, <TimestampColumn>)
    VALUES (NEW.<ForeignKeyValue>, NOW());
    ```
    !!! note
        For this example, ensure you have created a log table named `<LogTableName>` alongside your main table `<TableName>`. For guidance on creating a new table, please refer to [Manage Relational Databases with SQL Operations](task1.md){:target="_blank"}.

2. Examine the trigger by performing the action it's designed to respond to on the specified table.

    For example, after setting up a `AFTER INSERT` trigger to log a record in the log table *after insertion*, you can test the trigger's functionality by attempting to insert a record into the designated table and note the change in the log table. Execute the following command to observe the trigger in action:
    ``` sql
    INSERT INTO <TableName> (<ColumnName>, ...)
    VALUES ('anything', ...);
    ```

3. Verify that a log record has been created successfully by running the following command for the log table. 
    ``` sql
    SELECT * FROM <LogTableName>;
    ```

    This step verifies that the trigger is applied to the `AFTER INSERT` event.

## How to drop triggers
Finally, We will go over how to drop the trigger. 

1. Run the following command to drop the trigger in database.
    ``` sql
    DROP TRIGGER [IF EXISTS] <TriggerName>;
    ```

2. Repeat step 2 and 3 from `Create a BEFORE INSERT trigger` or `Create a AFTER INSERT trigger` to verify if trigger has been dropped.



## Conclusion
By the end of this section, you have gained knowledge on the following tasks:

- [x] Understanding the purpose and functionality of triggers
- [x] Creating BEFORE INSERT triggers
- [x] Creating AFTER INSERT triggers
- [x] Dropping triggers
