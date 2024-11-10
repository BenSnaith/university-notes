# Data Integrity and Constraints

## Integrity, why and how?

- (Logical) Data integrity is lost when things do not update in a consistent manner (remember data anomalies)
- Human errors or malicious acts
- It is ensured by applying various constraints
- Constrains relate to entities, domain or relationships and can be user-defined
- The majority of integrity constrains are addressed in DLL

## Entity Integrity

- Entity integrity relies on the use of primary keys
- Each tuple should be uniquely identified, and contain data related to that entity (aka no repeated data)
- In SQL, we use `PRIMARY KEY`

```SQL
CREATE TABLE department {
	dept_name VARCHAR(20),
	building VARCHAR(150),
	budget NUMBER(12, 2),
	PRIMARY KEY (dept_name)
};
```

## Data Integrity with an example

![[Untitled 57.png|Untitled 57.png]]

- PRIMARY KEYS CAN NEVER HAVE A NULL VALUE AND THEY MUST BE UNIQUE
- Note that foreign keys may have NULL values (for partial participation, maybe not all need to be in the other table)

## Domain Integrity

- Domain Integrity lists all allowable values for an attribute
- VARCHAR for 100 characters, DECIMAL of 4 digits and 2 decimal points, etc.

```SQL
CREATE TABLE course {
	course_id VARCHAR(7),
	title VARCHAR(50) NOT NULL,
	dept_name VARCHAR(20) NOT NULL,
	credits DECIMAL(2, 1) DEFAULT 1.5
	PRIMARY KEY (course_id)
};
```

## Domain Integrity in a detailed E-R diagram

- Domain integrity constrains are detailed in E-R diagrams

![[Untitled 1 35.png|Untitled 1 35.png]]

## Referential Integrity

- Also called foreign-key constraints, ensure that data is stored and used uniformly
- In SQL, we use FOREIGN KEY, REFERENCES

```SQL
CREATE TABLE course {
	course_id VARCHAR(7),
	title VARCHAR(50) NOT NULL,
	dept_name VARCHAR(20) NOT NULL,
	PRIMARY KEY (course_id),
	FOREIGN KEY (dept_name)
	REFERENCES department(dept_name)
};
```

- Not that `NOT NULL` for dept_name ensures full participation

## User-defined Constrains

- User-defined constrains are business rules that make sense in the context of the application, e.g:
    - A teacher cannot teach more than 3 modules per term
    - Any course’s number of credits cannot exceed 3.0

```SQL
CREATE TABLE course {
	course_id VARCHAR(7),
	title VARCHAR(50) NOT NULL,
	dept_name VARCHAR(20) NOT NULL,
	credits DECIMAL(2, 1) DEFAULT 1.5
												CHECK (credits <= 3.0),
	PRIMARY KEY (course_id)
};
```

- CHECK can be used to enforce such constraints

# The ACID properties and Transactions

## Definition of a Transaction

- A transaction is a collection of several instructions that form a single unit of work
- In practice, it is the execution of a sequence of SQL queries on the database that perform a high-level function
- The RDBMS must ensure that either the entire transaction is executed or none of its instructions

## Initiating a Transaction

- Transactions are initiated by the end-users using:
    - A high-level data-manipulation language (i.e. SQL)
    - A programming language with embedded database access capabilities (OBDC, JDBC)
- They are delimited by statements of the form begin transaction and end transaction
- They are indivisible; if one statement fails, any changes to the database must be undone
    - Statement failures (e.g. divide by 0), Operating System failure (e.g. Memory Loss), Hardware issues (e.g. IO errors)

## Transactions in Oracle

- DDL and DCL commands are auto-committed
- DML commands need to be managed by the end-user
- A transaction begins with the first DML command
- A transaction ends when
    - COMMIT or ROLLBACK are used
    - A DLL or DCL command is used (thus has to auto-commit)
    - Command editor exits normally
    - System crashes
- SAVEPOINT can be used as a marker for rolling back
    - ROLLBACK TO <name_of_savepoint>
- Auto-Commit can be turned on and off

## Transactions in Oracle - An Example

- An example of a transaction

```SQL
CREATE TABLE people (
	fname VARCHAR(15),
	lname VARCHAR(15),
	height NUMBER(3, 2),
	weight NUMBER(5, 2)
);
SAVEPOINT tbl_creation

INSERT INTO people VALUES ('Jenny', 'Evans', 1.67, 54);
SAVEPOINT data_insertions

SELECT * FROM people;

ROLLBACK TO tbl_creation;

SELECT * FROM people;
```

## Important Transaction Properties

- A transaction in a DBMS must maintain the ACID properties:
    - Atomicity: “all-or-none”, a transaction must be treated as an atomic unit and must leave the database in a healthy state
    - Consistency: “all seem correct”, the state of the database after the transaction must be healthy, and data must be consistent
    - Isolation: “as if alone”, all statements of a transaction must execute no matter how many other transactions or single queries are performed in parallel
    - Durability: “prone to failures”, the database must be able to return to a healthy state after a crash or a failure, completing any affected transactions

## A practical example

- Scenario: “Transferring money from account A to account B in a very simple back application”
- We will assume only read, write and simple arithmetic operations are possible
- Consider the following transaction

```SQL
T: read(A);
	A := A - 100;
	write(A);
	read(B);
	B := B + 100;
	write(B);
```

- If the database crashes after line 3, the resulting state will not reflect the state of the world, it will be an inconsistent state
- Inconsistent states occur during transactions but are replaced by consistent states
- The recovery system of the DBMS is able to keep track of the values that are changed, so it can recover if needed

### Consistency

- Data Consistency: automatically testing for data and referential integrity constraints
- Transaction consistency: high-level constraints thus the responsibility of the application programmer
- The consistency requirement is that the sum of A and B does not change after the transaction

### Isolation

- The state of the database is temporarily inconsistent between lines 3-6
- Note that executing transactions serially may solve this problem, but concurrent transactions provide significant performance benefits

### Durability

- If the transaction completes successfully after line 6, any changes to the database must persist
- Failures may cause memory less (thus some instructions may fail), but a successful transaction must imply that changes are written on disk
- The recovery system is able to reconstruct transaction changes, when the system is restarted after a failure

## Storage Structures and System Failures

- There are three categories for storage structures used by DBMS
    - Volatile Storage: main memory, cache memory does not survive failures but provides fast and direct access to data
    - Non-volatile storage: Mainly all secondary and tertiary storage: HDDs, SSDs, USB flash, CD/DVDs, floppy, magnetic tape and tape libraries. Survives system crashes but prone to loss of information
    - Stable Storage: (i) on-line implementations for data redundancy (e.g. RAID mirroring), (ii) off-line consists of multiple copies of the same disk placed at different secure locations. ALWAYS survives with no loss of data

## Ensuring Transaction Atomicity: Shadow Paging

- Shadow paging, conceived by IBM, was very popular approach in the 80s
    - The DBMS makes a copy of the pages a transaction is about to change
    - If the transaction is successful, the copy becomes the original (and visible to other users)
    - Too slow and problematic
    - Today only a few DBMS use it still (e.g. CouchDB, OpenLDAP’s database backend)

## Ensuring Transaction Atomicity: Logging

- Logging is the most common approach
    - The DBMS records all actions so it can undo them if the transaction is aborted
    - Undone records are maintained in both volatile and non-volatile storage (similar to the blackbox of an airplane)
- Logging at that level is used by almost everyday DBMS
- In addition to rolling back in atomicity, it has more benefits
    - Auditing
    - Efficiency Reasons

## Ensuring Transaction Consistency

- Remember that we try to make sure that the following statement holds:
    
    “If what is represented by the database is logically correct, then any SQL queries sent to this database will produce logical results sets”
    
- We ensure data consistency by enforcing domain integrity and primary-foreign key constraints
- We rely upon the application programmer for transaction consistency

## Ensuring Transaction Isolation

- From the end-users point, there needs to be an exclusive access to the database
    - A transaction is submitted, and is executed as if it is running by itself
- But concurrency is achieved by interleaving the transactions

## Concurrency Example

- In the back account scenario, A and B each have £600
    - T1: transfer £50 from A to B
    - T2: credit both A and B with 6% interest
- How many possible outcomes can result from T1 and T2
- There is no guarantee that either T1 or T2 will execute before the other, if they are submitted together
- But the net effect should be equivalent, i.e. the consistency constraint A + B = 1272 must hold no matter the order
    - A = 583, B = 689, A + B = 1272
    - A = 586, B = 686, A + B = 1272
- The outcome depends on whether T1 executes before T2 and vice versa

## Concurrency using Serial Schedules

- Two equivalent serial schedules are possible for T1 and T2

![[Untitled 2 33.png|Untitled 2 33.png]]

## Concurrency using Interleaving

- Serial schedules are slow due to disk and network I/O
- Interleaving: when one transaction stalls, another continues

![[Untitled 3 31.png|Untitled 3 31.png]]

## Bad Schedules due to Interleaving

![[Untitled 4 28.png|Untitled 4 28.png]]

## Discussion on Interleaving

- Interleaving is a neat method to allow transactions happen
- BUT they are prone to conflicts
    - Instructions that belong to different transactions
    - Instructions that affect the same object (tuple), and at least one of the is a write (R-W, W-R, W-W)
- Interleaving can only work if the transactions can be considered conflict serialisable
- Not all of the are, but there are algorithms to allow us identify conflicting ones

## Example of R-W conflict

- Schedule leading to unrepeatable reads due to atomicity and consistency issues
- Assume that the initial value of A = £600

![[Untitled 5 28.png|Untitled 5 28.png]]

## Example of W-R conflict

- Schedule leading to reading uncommitted data (aka causes dirty reads)

![[Untitled 6 23.png|Untitled 6 23.png]]

- T1 has to abort and rollback to a consistent state
- T2 assumed A = 800 (uncommitted)

## Example of W-W conflict

- Schedule leading to overwriting uncommitted data

![[Untitled 7 22.png|Untitled 7 22.png]]

- Both T1 and T2 make changes to A and B
- A and B should be modified atomically

## Solutions available in DBMS’s

- Concurrency and recovery are among the most important features offered by a DBMS
- Concurrency Control is automatic
    - The DBMS automatically inserts lock/unlock requests and schedules actions for different transactions
    - In ensures that the resulting transactions’ execution is equivalent to executing them one after the other is some order
- Protocols such as the Two-Phase Locking are in place

[[Week 6 - Lecture Notes]]