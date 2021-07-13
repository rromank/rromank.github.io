## UNIQUE Constraint

The `UNIQUE` constraint specifies that each non-NULL value in the constrained column must be unique.

#### Details

* You can insert NULL values into columns with the UNIQUE constraint because NULL is the absence of a value, so it is never equal to other NULL values and not considered a duplicate value. This means that it's possible to insert rows that appear to be duplicates if one of the values is NULL.
  
  If you need to strictly enforce uniqueness, use the NOT NULL constraint in addition to the UNIQUE constraint. You can also achieve the same behavior through the table's Primary Key.
  
* Columns with the `UNIQUE` constraint automatically have an index created with the name `<table name>_<columns>_key`. To avoid having two identical indexes, you should not create indexes that exactly match the `UNIQUE` constraint's columns and order.
  
  The `UNIQUE` constraint depends on the automatically created index, so dropping the index also drops the `UNIQUE` constraint.
  
* When using the `UNIQUE` constraint on multiple columns, the collective values of the columns must be unique. This does not mean that each value in each column must be unique, as if you had applied the `UNIQUE` constraint to each column individually.

* You can define the `UNIQUE` constraint when creating a table, or you can add it to existing tables through `ADD CONSTRAINT`