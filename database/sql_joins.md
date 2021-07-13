## SQL Join types

1. Inner Join, Equi Join, natural join
2. Self Join
3. Outer Join
   * Left Outer Join
   * Right Outer Join
   * Full Outer Join
4. Cross join


#### Inner Join, Equi Join, natural join

An equi-join is used to match two columns from two tables using explicit operator =

```sql
select *
  from table1 T1, table2 T2
  where T1.column_name1 = T2.column_name2
```

An inner join is used to get the cross product between two tables, combining all records from both tables. To get the right result you can use a equi-join or one natural join (column names between tables must be the same)

```sql
select *
  from table1 T1 INNER JOIN table2 T2
  on T1.column_name = T2.column_name
```

Natural join

```sql
select *
  from table1 T1 NATURAL JOIN table2 T2
```

#### Self join

A self join allows you to join a table to itself. It is useful for querying hierarchical data or comparing rows within the same table.

A self join uses the inner join or left join clause. Because the query that uses self join references the same table, the table alias is used to assign different names to the same table within the query.

```sql
SELECT
    select_list
FROM
    T t1
[INNER | LEFT]  JOIN T t2 ON
    join_predicate; 
```

The query references the table T twice. The table aliases t1 and t2 are used to assign the T table different names in the query.

#### Left Join (Left Outer Join)

The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.

**Note:** In some databases LEFT JOIN is called LEFT OUTER JOIN.

```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```

![left join](https://www.w3schools.com/sql/img_leftjoin.gif)

#### Right Join (Right Outer Join)

The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.

**Note:** In some databases RIGHT JOIN is called RIGHT OUTER JOIN.

```sql
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```

![right join](https://www.w3schools.com/sql/img_rightjoin.gif)

#### Full Outer Join

The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.

**Tip:** FULL OUTER JOIN and FULL JOIN are the same.

```sql
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

![right join](https://www.w3schools.com/sql/img_fulljoin.gif)

#### Cross Join

In SQL, the CROSS JOIN is used to combine each row of the first table with each row of the second table. It is also known as the Cartesian join since it returns the Cartesian product of the sets of rows from the joined tables.

![cross_join](https://www.educative.io/api/edpresso/shot/5392077896548352/image/5672062263754752)

**Syntax**

There are two implementations of the CROSS JOIN statement:

1. Using the CROSS JOIN syntax.

```sql
SELECT      [column names]
FROM        [Table1]
CROSS JOIN  [Table2]
```

2. Using the FROM clause without using a WHERE clause.

```sql
SELECT [column names]
FROM   [Table1], [Table2]
```


