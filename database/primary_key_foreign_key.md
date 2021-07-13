#### Primary Key

A primary key is a special relational database table column (or combination of columns) designated to uniquely identify each table record.

A primary key is used as a unique identifier to quickly parse data within the table. A table cannot have more than one primary key.

A primary key’s main features are:

* It must contain a unique value for each row of data.
* It cannot contain null values.
* Every row must have a primary key value.

A primary key might use one or more fields already present in the underlying data model, or a specific extra field can be created to be the primary key.

##### Should each and every table have a primary key?

Short answer: yes.

Long answer:

You need your table to be joinable on something
* If you want your table to be clustered, you need some kind of a primary key.
* If your table design does not need a primary key, rethink your design: most probably, you are missing something. Why keep identical records?
* In MySQL, the InnoDB storage engine always creates a primary key if you didn't specify it explicitly, thus making an extra column you don't have access to.

Note that a primary key can be composite.

If you have a many-to-many link table, you create the primary key on all fields involved in the link. Thus you ensure that you don't have two or more records describing one link.

Besides the logical consistency issues, most RDBMS engines will benefit from including these fields in a unique index.

And since any primary key involves creating a unique index, you should declare it and get both logical consistency and performance.


#### Foreign Key

A foreign key is a column or group of columns in a relational database table that provides a link between data in two tables. It acts as a cross-reference between tables because it references the primary key of another table, thereby establishing a link between them.

The majority of tables in a relational database system adhere to the foreign key concept. In complex databases and data warehouses, data in a domain must be added across multiple tables, thus maintaining a relationship between them. The concept of referential integrity is derived from foreign key theory.

Foreign keys and their implementation are more complex than primary keys.

##### Explanation

While a primary key may exist on its own, a foreign key must always reference to a primary key somewhere. The original table containing the primary key is the parent table (also known as referenced table). This key can be referenced by multiple foreign keys from other tables, known as “child” tables.

For any column acting as a foreign key, a corresponding value should exist in the linked table. Special care must be taken while inserting data and removing data from the foreign key column, as a careless deletion or insertion might destroy the relationship between the two tables.

If the integrity between the two databases is compromised, errors may ensue.

##### Referential actions associated with foreign key

* Cascade

  When rows in the parent table are deleted, the matching foreign key columns in the child table are also deleted, creating a cascading delete.
  
* Set Null

  When a referenced row in the parent table is deleted or updated, the foreign key values in the referencing row are set to null to maintain the referential integrity.
  
* Triggers

  Referential actions are normally implemented as triggers. In many ways foreign key actions are similar to user-defined triggers. To ensure proper execution, ordered referential actions are sometimes replaced with their equivalent user-defined triggers
  
* Set Default

  This referential action is similar to "set null." The foreign key values in the child table are set to the default column value when the referenced row in the parent table is deleted or updated
  
* Restrict

  This is the normal referential action associated with a foreign key. A value in the parent table cannot be deleted or updated as long as it is referred to by a foreign key in another table.
  
* No Action

  This referential action is similar in function to the "restrict" action except that a no-action check is performed only after trying to alter the table.