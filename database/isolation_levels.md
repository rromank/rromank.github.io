## Transaction isolation level

https://docs.microsoft.com/en-us/sql/odbc/reference/develop-app/transaction-isolation-levels?view=sql-server-ver15

| Transaction isolation level | Dirty reads | Non-repeatable reads | Phantoms |
|-----------------------------|-------------|----------------------|----------|
| Read uncommitted            |      X      |          X           |    X     |
| Read committed              |     ---     |          X           |    X     |
| Repeatable read             |     ---     |         ---          |    X     |
| Serializable                |     ---     |         ---          |   ---    |

Dirty Reads A dirty read occurs when a transaction reads data that has not yet been committed. For example, suppose transaction 1 updates a row. Transaction 2 reads the updated row before transaction 1 commits the update. If transaction 1 rolls back the change, transaction 2 will have read data that is considered never to have existed.

Nonrepeatable Reads A nonrepeatable read occurs when a transaction reads the same row twice but gets different data each time. For example, suppose transaction 1 reads a row. Transaction 2 updates or deletes that row and commits the update or delete. If transaction 1 rereads the row, it retrieves different row values or discovers that the row has been deleted.

Phantoms A phantom is a row that matches the search criteria but is not initially seen. For example, suppose transaction 1 reads a set of rows that satisfy some search criteria. Transaction 2 generates a new row (through either an update or an insert) that matches the search criteria for transaction 1. If transaction 1 reexecutes the statement that reads the rows, it gets a different set of rows.

## ACID

These four properties are also known as ACID principles. Let’s briefly explain these four principles.

##### Atomicity
This property is also known as all or nothing principle. According to this property, a transaction can not be completed partially, so if a transaction gets an error at any point of the transaction, the entire transaction should be aborted and rollbacked. Or, all the actions contained by a transaction must be completed successfully.

##### Consistency
According to this property, the saved data must not damage data integrity. This means that the modified data must provide the constraints and other requirements that are defined in the database.

##### Durability
According to this property, the committed will not be lost even with the system or power failure.

##### Isolation
The database transactions must complete their tasks independently from the other transactions. This property enables us to execute the transactions concurrently on the database systems. So, the data changes which are made up by the transactions are not visible until the transactions complete (committed) their actions. The SQL standard describes three read phenomena, and they can be experienced when more than one transaction tries to read and write to the same resources.

* Dirty-reads
* Non-repeatable reads
* Phantom reads
