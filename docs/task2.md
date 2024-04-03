# How to join tables into a view for future reference



## Overview
Understanding how to join tables is crucial for effectively managing a relational database, where data resides across multiple tables. A view in a database serves as a virtual table, formed by a query that selects data from multiple sources. This virtual table can be saved for future reference, making views invaluable for data analysis and reporting by providing access to combined data without the need for data duplication.


## Setting up tables to join
Before getting started, ensure tables we intend to join are properly prepared, and that a referential relationship, usually defined by foreign keys, is established between them. This step is crucial for accurately and efficiently merging data based on common columns.

1. Follow instructions in [How to create, manipulate, and drop a SQL table](task1.md){:target="_blank"} to create some tables and insert some data.

    !!! note
        We need **at least two tables**, each with at least one column that relates to the other table.


2. Verify that the correct table was made by running the following command for all the tables created in step 1. 
    ```
    SELECT * FROM <TableName>;
    ```
    The ```SELECT``` command chooses which columns to include in the returned table. The ```*``` symbol means to include all records. The ```FROM``` command tells SQL which table to query from.

    At this point, you should see that a new table is made 
    ![Image title](https://dummyimage.com/600x400/eee/aaa)

## How to combine multiple tables
After preparing multiple tables for joining, you need to decide how to join them. Here are the most common types of SQL joins:

### Combine tables with INNER JOIN
1. Execute the command below to perform inner join on two tables.
    ```
    SELECT <TableName1>.<ColumnName>, <TableName2>.<ColumnName>       // Replace <TableName1> and <TableName2> with the names of your tables, <ColumnName> with the names of the columns you want to select, and <CommonColumnName> with the name of the column used to relate both tables.
    FROM <TableName1>
    INNER JOIN <TableName2>
    ON <TableName1>.<CommonColumnName> = <TableName2>.<CommonColumnName>;
    ```

    !!! note
        ColumnNames in both tables should represent the same data.

    At this point, you should see the combined table in the output box. 
    ![Image title](https://dummyimage.com/600x400/eee/aaa)

2. Verify that the combined table was merged correctly by cross checking the result. 

    Verify the row count in the combined table to ensure it matches the expected number of matched records. Additionally, confirm that all desired columns are present in the combined table.

### Combine tables with LEFT JOIN
1. Execute the command below to perform inner join on two tables.
    ```
    SELECT <TableName1>.<ColumnName>, <TableName2>.<ColumnName>       // Replace <TableName1> and <TableName2> with the names of your tables, <ColumnName> with the names of the columns you want to select, and <CommonColumnName> with the name of the column used to relate both tables.
    FROM <TableName1>
    LEFT JOIN <TableName2>
    ON <TableName1>.<CommonColumnName> = <TableName2>.<CommonColumnName>;
    ```

    !!! note
        ColumnNames in both tables should represent the same data.

    At this point, you should see the combined table in the output box. 
    ![Image title](https://dummyimage.com/600x400/eee/aaa)

2. Verify that the combined table was merged correctly by cross checking the result. 

    Verify the row count in the combined table to ensure it matches the total rows in table `<TableName1>`. Additionally, confirm that all desired columns are present in the combined table.

## How to create a view in the database
After you combined data from multiple tables, you will need to create a view for the combined data to store in the database for future reference. 

1. Execute the command below to create a view.
    ```
    CREATE VIEW <ViewName> AS         // Replace <ViewName> with the name of your view
    <JoinQuery>;                      // Replace <JoinQuery> with your join query;
    ```

    In the command provided, replace `<JoinQuery>` with the join query you crafted in the previous step. 

2. Verify that the correct table was made by running the following command. 
    ```
    SELECT * FROM <ViewName>;         // Replace <ViewName> with the name of your view
    ```
    The ```SELECT``` command chooses which columns to include in the returned table. The ```*``` symbol means to include all records. The ```FROM``` command tells SQL which table to query from.

    Make sure the query results match those from the join query in the `How to combine multiple tables` section.

3. Follow instructions in [How to create, manipulate, and drop a SQL table](task1.md){:target="_blank"} to update a record in one of the original tables. 

4. Refer to step 2 in this section to verify that the view's content has indeed updated to mirror the changes made to the original table.

    Observe how the view automatically updates to reflect these changes, showcasing its dynamic connection to the source data.

## How to drop views
Finally, We will go over how to drop the view. 

1. Run the following command to drop the view in database.
    ```
    DROP VIEW [IF EXISTS] <ViewName>;
    ```



## Conclusion
By the end of this section, you have gained knowledge on the following tasks:

- [x] Understanding the purpose and utility of joining tables
- [x] How to create a view from joined tables
- [x] How to combine table with "INNER JOIN"
- [x] How to combine table with "LEFT JOIN"
- [x] How to drop views in database
