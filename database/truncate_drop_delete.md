## Truncate, Drop, Delete

#### TRUNCATE

TRUNCATE Command is a Data Definition Language operation. It is used to remove all the records from a table. It deletes all the records from an existing table but not the table itself. The structure or schema of the table is preserved.

Truncate command marks the table for deallocation. This operation removes all the data from a table bypassing a number of constraints enforced on the table. MySQL does not allow the users to truncate the table which is referenced as FOREIGN KEY in another table.

> TRUNCATE TABLE statement is a DDL command so it **can not be rolled back**.
  The Truncate command resets the AUTO_INCREMENT counters on the table.
  MySQL truncates the table by dropping and creating the table. Thus, the DELETE triggers for the table do not fire during the truncation.
  
##### Syntax

```sql
TRUNCATE TABLE [database_name.]table_name;
[database_name.] is optional. It is used to specify the name of the database in which the table exists.


[table_name] specifies the name of the table we want to truncate.
```


#### DELETE

The DELETE statement in SQL is a Data Manipulation Language(DML) Command. It is used to delete existing records from an existing table. We can delete a single record or multiple records depending on the condition specified in the query.

> The conditions are specified in the WHERE clause of the DELETE statement. If we omit the WHERE clause then all of the records will be deleted and the table will be empty.

The DELETE statement scans every row before deleting it. Thus it is slower as compared to TRUNCATE command. If we want to delete all the records of a table, it is preferable to use TRUNCATE in place of DELETE as the former is faster than the latter.

> DELETE is a DML Command so it can be rolled back.

The DELETE command returns the number of records that were deleted by its execution.

##### Syntax

```sql
DELETE FROM table_name [WHERE conditions];
table_name specifies the name of the table from which we want to delete the records.
[WHERE condirions] is optional. We can provide conditions to filter out the records to be deleted.
```


#### DROP

DROP statement is a Data Definition Language(DDL) Command which is used to delete existing database objects. It can be used to delete databases, tables, views, triggers, etc.

A DROP statement in SQL removes a component from a relational database management system (RDBMS).

> DROP is a DDL Command. Objects deleted using DROP are permanently lost and it cannot be rolled back.

Unlike TRUNCATE which only deletes the data of the tables, the DROP command deletes the data of the table as well as removes the entire schema/structure of the table from the database.

##### Syntax

```sql
DROP object object_name
object: Keyword representing the type of the database object.
object_name: It specifies the name of the object we want to delete.
```
