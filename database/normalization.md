## Normalization

Normalization is used for mainly two purposes,

* Eliminating redundant(useless) data.
* Ensuring data dependencies make sense i.e data is logically stored.


### Problems Without Normalization

If a table is not properly normalized and have data redundancy then it will not only eat up extra memory space but will also make it difficult to handle and update the database, without facing data loss. Insertion, Updation and Deletion Anomalies are very frequent if database is not normalized

#### Update Anomaly

Update Anomaly: Let say we have 10 columns in a table out of which 2 are called employee Name and employee address. Now if one employee changes it’s location then we would have to update the table. But the problem is, if the table is not normalized one employee can have multiple entries and while updating all of those entries one of them might get missed.

#### Insertion Anomaly

Let’s say we have a table that has 4 columns. Student ID, Student Name, Student Address and Student Grades. Now when a new student enroll in school, even though first three attributes can be filled but 4th attribute will have NULL value because he doesn't have any marks yet.

#### Deletion Anomaly

This anomaly indicates unnecessary deletion of important information from the table. Let’s say we have student’s information and courses they have taken as follows (student ID,Student Name, Course, address). If any student leaves the school then the entry related to that student will be deleted. However, that deletion will also delete the course information even though course depends upon the school and not the student.

---
### Normal forms

* First normal form(1NF)
* Second normal form(2NF)
* Third normal form(3NF)
* Boyce & Codd normal form (BCNF)

#### First normal form (1NF)
http://www.gitta.info/LogicModelin/en/html/DataConsiten_Norm1NF.html

A relation is in first normal form if every attribute in every row can contain only one single (atomic) value.

#### Second normal form (2NF)
http://www.gitta.info/LogicModelin/en/html/DataConsiten_Norm2NF.html

For a table to be in the Second Normal Form,

It should be in the First Normal form.
And, it should not have Partial Dependency.

> A relation that is in First Normal Form and every non-primary-key attribute is fully functionally dependent on the primary key, then the relation is in Second Normal Form (2NF).

#### Third normal form (3NF)
http://www.gitta.info/LogicModelin/en/html/DataConsiten_Norm3NF.html

A relation is in third normal form if it is in 2NF and no non key attribute is transitively dependent on the primary key.


#### Boyce and Codd Normal Form (BCNF)

Boyce and Codd Normal Form is a higher version of the Third Normal form. This form deals with certain type of anomaly that is not handled by 3NF. A 3NF table which does not have multiple overlapping candidate keys is said to be in BCNF. For a table to be in BCNF, following conditions must be satisfied:

R must be in 3rd Normal Form
and, for each functional dependency ( X → Y ), X should be a super Key.

https://habr.com/ru/company/mailru/blog/501598/
https://habr.com/ru/post/254773/


