# From Data to Databases

## What is data?

- Data is the raw fact, that on their own have no meaning
- Any alphanumerical character, i.e. text, numbers and symbols
- Examples;
    - YES, NO, NO, YES, YES, YES
    - 42, 65, 19, 143. 0
    - “CS1IAD”, “CS1OOP”, “CS1PSA”

## Data to information

- Data needs to be processed and turned into meaningful information
- It needs to be structured and presented in a given context

![[Untitled 55.png|Untitled 55.png]]

- Knowledge is the understanding of rules needed to interpret information
- The capacity of understanding relationships between pieces of information
- What to actually do with the information

## Database System Applications

- In everyday live, database system applications manage collections of data that are highly valuable, relatively large and accessed by multiple users and other applications
- Data, and not the calculations, is the central aspect
    - What is twitter without data

# Architecture of Database Systems Applications

- Earlier generation (a) vs modern-generation (b)

![[Untitled 1 33.png|Untitled 1 33.png]]

## Storing data needs structure and rules

A data model is a collection of conceptual tools that define the data structure, relationships, semantics and consistency constraints

  

We will look at:

- Relationship Model: tabular format to accommodate data and represent relationships
- Entity-Relationship Model: for database design using a collection of objects (entities) that have relationships with each other

## Database Terminology

- A database system or database management system (DBMS) is a collection of interrelated data and a set of programs to access those data
- The collection of data is usually referred to as a database
- A relational database is based on the relational model
- The SQL language is used to interact with the database
- The database administrator (DBA) has the central control over a database system

# The Relational Model

## Data Organisation in Relational Modelling

![[Untitled 2 31.png|Untitled 2 31.png]]

## Fundamentals of the Relational Model

- Tables are used to structure the data related to a concept of reality, i.e. a university lecturer
- Unique table columns describe variables related to the concept
- Rows represent the relationship among a list of values (n-tuple of values)
- In the relational model the term relation is used for a table, tuple for a row, and attribute for a column

## Properties of Relations

- Relations of the same design have distinct names
- Each attribute has a distinct name
- Values of an attribute are all in the same domain
- Each cell in the relations contains exactly one atomic value
- Each tuple is distinct; there are no duplicate tuples
- No order for attributes or tuples
- Keys are used to uniquely identify tuples

## Types of Keys

- Need to specify a method to distinguish tuples within a relation
- Attribute values can be used to uniquely identify a tuple
- A superkey is a set of one or more attributes which offers that uniqueness
    - e.g. {ID}, {ID, name}, {ID, dept_name}, etc, all are superkeys
- A candidate key is a minimal superkey for which no proper subset is a superkey
    - A relation may have multiple candidate keys. e.g. {ID} and {name, dept_name} are both candidate keys, whereas {ID, Name} is not

## Primary Keys in Relations

- The database designer decides the primary key
- Primary keys are referred to as primary key constraints and are usually listed first
    - e.g. instructor(ID, name, dept_name, salary) or instructor(name, dept_name, ID, salary)
- Primary keys should be chosen wisely and w.r.t, what is modelled in the real-world
- A surrogate key may be used when a natural, or real, private key is not possible
    - e.g. {ID} with auto-increment

## Foreign Keys in Relations

![[Untitled 3 29.png|Untitled 3 29.png]]

- A foreign key constraint ensure that the value of an attribute of a relation matches the value of the primary key of some other relation
- e.g. {instructor.dept_name} is a foreign key referencing {department.dept.name}

# The Entity-Relationship Model

## Entity Representation

- Entities represent distinctly identifiable terms or “things”
    - e.g. a student, a university, a module
- They are related in a variety of ways
    - e.g. an instructor teaches a model

## The Entity-Relationship Data Model

- The E-R model expresses the overall database design graphically
- Three main components: entities, attributes and relationships

## Entities and Attributes in E-R Diagrams

- Underlined primary key in both notations

![[Untitled 4 26.png|Untitled 4 26.png]]

## Relationships

- A relationship is an association among several entities
    - e.g. instructor Katz is associated with two students Shankar and Zhang

![[Untitled 5 26.png|Untitled 5 26.png]]

## Relationship in E-R Diagrams

- A relationship is depicted by a diamond that links different related entities

![[Untitled 6 21.png|Untitled 6 21.png]]

- Entities participate in relationships, e.g. two entities participate in a binary relationship

## Mapping Cardinalities

- Given the binary relationship between two entity sets, A and B, there can be only one of the following mapping cardinalities:
    - one-to-one: an entity A is associated with at most one entity in B, visa versa
    - one-to-many: entity A is associated with any number of entities in B, whereas entities in B have one-to-one associations with entities in A
    - many-to-one: entities in A have a one-to-one association with entities in B, whereas entities in B have a one-to-many association with entities in A
    - many-to-many: an entity in A is associated with and number of entities in B and visa versa.

![[Untitled 7 20.png|Untitled 7 20.png]]

## Mapping Cardinalities in E-R Diagrams

- The participation of an entity set A in a relationship is total, and depicted with double lines, when all entities in A participate in that relationship — partial otherwise

![[Untitled 8 19.png|Untitled 8 19.png]]

- Cardinality limits or multiplicities are used to depict complex relationships using the syntax of (min, MAX): e.g. (0..*), (0..1), (1..1), (1..*), etc.

![[Untitled 9 18.png|Untitled 9 18.png]]

## Relationships to Relations

- A many-to-many relationship is represented by a new relation with attributes the primary keys of the two involved relations and any descriptive attributes of the relationship
    - advisor(instructor_ID, student_ID, allocation_date)
    - Total many-to-one and one-to-many relationships can be represented by adding an extra to the “many” side containing the primary key of the “one” side
        - department(dept_name, building, budget)  
            instructor(ID, name, salary, dept_name)  
            
    - For one-to-one relationships, either side can be chosen to act as the “many” side; an extra attribute can be added to either of the relations corresponding to the two entities
    - For partial participation on the “many” side, allow the use of null values.

# Introduction to SQL

## Why use SQL?

- It allows database management and manipulation tasks
- It is universal and portable and easy to learn
- It powers the most commonly used RDBMS
- It is the most popular language across desktop and web devs, sys admins, and data scientists

## The important SQL parts

- Data Definition Language (DDL): provides commands for defining and manipulating relational databases, as well as specifying integrity constraints
- Data Manipulation Language (DML): provides the ability to query the database, and to insert, delete and modify tuples in relations
- Data Control Language (DCL): defines and manipulates access control of the database
- Transaction Control Language (TCL): provides commands for dealing with transactions

## SQL statements

- SQL statements may be multi-line, but have to finish with a semi-colon

```SQL
CREATE TABLE department {
	dept_name VARCHAR(20),
	building VARCHAR(150),
	budget DECIMAL(12, 2),
	PRIMARY KEY (dept_name)
};
```

- All components are case insensitive, except for literal strings  
    SeLecT * FROM department  
    where dept_name = ‘CompSci’;  
    

## Create Relations

- Creating a department relation

```SQL
CREATE TABLE department {
	dept_name VARCHAR(20),
	building VARCHAR(15) NOT NULL,
	budget INT NOT NULL,
	monthly_allow DOUBLE AS (budget/12),
	PRIMARY KEY (dept_name)
};
```

- Creating a course relation

```SQL
CREATE TABLE course {
	course_id VARCHAR(7),
	title VARCHAR(50) NOT NULL,
	dept_name VARCHAR(20) NOT NULL,
	credits INT DEFAULT 10,
	PRIMARY KEY (course_id),
	FOREIGN KEY (dept_name) REFERENCES department(dept_name)
};
```

## Dropping Relations

- Dropping a relation from the database is a drastic action

```SQL
DROP TABLE course;
```

- If referential constrains are in place, then the drop is cancelled

```SQL
DROP TABLE department;
```

e.g. if course exists, department cannot be deleted  
Error: unique/primary keys table is referenced by foreign keys  

- The following clause will allow dropping referenced relations

```SQL
DROP TABLE department CASCADE CONSTRAINT;
```

## Inserting Tuples

- Insert tuples by using the relation’s definition order, e.g.

```SQL
CREATE TABLE department {
	dept_name VARCHAR(20),
	building VARCHAR(15) NOT NULL,
	budget DECIMAL(12, 2) NOT NULL,
	monthly_allow DECIMAL(12, 2) AS (budget/12),
	PRIMARY KEY (dept_name)
};
```

- Insert tuples by specifying the attributes and their order

```SQL
INSERT INTO department(building, dept_name, budget)
VALUES ('MB', 'Geography', 1100000);
```

## Updating Tuples

- “A salary increase of 2% is to be paid to all instructors with a salary less that 80k

```SQL
UPDATE instructor SET salary = salary * 1.02
WHERE salary < 80000;
```

- Updating multiple attributes is also possible

```SQL
UPDATE department SET building ='AC', budget = 1600000
WHERE salary < 80000;
```

## Deleting Tuples

- “Delete all tuples of instructors, whose salary is between 85k and 100k”

```SQL
DELETE FROM instructor WHERE salary BETWEEN 85000 AND 100000;
```

- Deletion will fail if any of instructor’s columns are referred to by a foreign key of another relation

## Learning Resources

- SQL Tutorial: w3schools
- LiveSQL: Oracle

## Lecture Notes

A superkey is a key that can idetify tuples uniquely

A candidate is a superkey with minimal attributes

A primary key is the key choosen to idetify tuples in the DB