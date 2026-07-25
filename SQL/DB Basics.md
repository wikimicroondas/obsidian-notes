## What is a database
A database is a type of structured file made with the purpose of `organize` and `retrieve` data through very high optimized math algorithms. The data is compressed and stored as `binaries` in lieu of plain text, and then it is managed by a `Database Managment System` (DBMS).

## Database Management System
> It is a type of software that allows users to define, create and control data.

Its main goal is to orchestrate the database. We interact with it through its interface. This interface is designed to help people work with different types of databases without exposing their actual differences. 

## Database standards
The reason why we use `SQL` language it's because it provides us:
* `schemas`    - Describes how you organize the data.
* `metadata`  - Holds structural and statistical information.

Also it grants:
* Remote access from multiple devices.
* Set up tests and constraints.
* Access restriction via login/password authentication.
* Data consistency through schemas `rules`. This allows the DB to restore information and manage concurrent updates.
* Conflict solving configuration (merge conflict solving).
* Scheduled backups.

## Database transactions
> A transaction is a meaningful operation that can only be performed completely

Interacting with the database implies to secure that a complex operation is contemplated through all of its phases. If every part of it succeed, then we `commit` the operation, if it fails, we `rollback` to a consistent state.

To fulfill this we use `ACID properties`.
* **Atomicity**
	All operations must be successful. If any of them fail, the entire transaction fails. This property is ensured by the transaction recovery subsystem of a DBMS.

* **Consistency**
	The result must be reliable. Any transaction will take the database from one valid state to another and there would be no middle-states.

* **Isolation**
	We must separate each phase of the transaction. Every transaction has a well-defined boundary.

* **Durability**
	Data modifications that occur within a successful transaction are kept permanently within the system, regardless of what else occurs.

### State of transactions
During its life cycle, any transaction passes through several different states.

| State              | Description                                                                                                  |
| ------------------ | ------------------------------------------------------------------------------------------------------------ |
| Active             | The transaction has been executed. In this state read/write operations can be performed.                     |
| Partially commited | Some operations have been successful, but no permanent changes have been made against the database.          |
| Failed state       | One operation encountered errors, or the permanent change was a failure.                                     |
| Aborted            | Failed state -> Aborted. The changes are deleted or rolled back to the database's previous consistent state. |
| Commited           | All of the operations were successfully executed and the changes were made permanent against the database.   |
> There are more transaction's states than the ones shown in this example.

These transactions follow a `concurrent` design, this means that all of the information that is being processed is locked from executing other operations until it ends.

