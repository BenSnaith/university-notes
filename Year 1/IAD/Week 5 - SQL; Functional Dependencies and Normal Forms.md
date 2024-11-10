# Database anomalies

## What is a “good” database design

- The goal of database design is to ultimately create a set of relations that allow us to:
    - store data without unnecessary redundancy
    - retrieve data efficiently and easily
- A bad design renders a database prone to anomalies
- We fight data redundancy by applying normalisation

## Database Anomalies: Insertion

Insertion anomaly:

- Storing incomplete information due to multiple concepts in rows

![[Untitled 56.png|Untitled 56.png]]

- Adding Shen as a new tutor leads to incomplete cells, affecting consistency, integrity and access of that data

## Database Anomalies: Update

Update anomaly:

- Updating specific values affects data integrity due to duplications

![[Untitled 1 34.png|Untitled 1 34.png]]

- Changing tutor for James Thompson requires two different database updates

## Database Anomalies: Deletion

Deletion anomaly:

- Deleting rows may unintentionally remove important data

![[Untitled 2 32.png|Untitled 2 32.png]]

- Removing Fang Chen from the table will also remove his tutor’s data

## Summary on database anomalies

- If the database is not well designed, the overall data integrity will deteriorate over time
- Anomalies occur due to data redundancy and/or lack of proper constraints
- Flat-file databases almost always lead to anomalies
- Breaking flat-file databases into smaller, focused and well maintained tables is the only cure

# Scheme decomposition and SQL Joins

## Universal Relation

- The universal relation assumption
    - All data attributes can be stored into a single table, which can be decomposed into smaller tables (schema decomposition)
    - Then SQL `SELECT` statements can `JOIN` smaller tables together to retrieve and present data
- Two questions:
    - How do we `JOIN` tables together?
    - How do we decompose a table into smaller ones?

## JOIN Expressions

- The `JOIN` operation takes two relations and returns one, given that tuples in the given relation match under some condition
- It is typically used as a subquery expression in the `FROM` part of the `SELECT` query

## JOIN Expressions - Tutors and Tutees

- Consider the relations Tutor (left) and Tutee (right)

![[Untitled 3 30.png|Untitled 3 30.png]]

- Note that there are tutors who have no tutees, e.g. John, and tutees that are not assigned to a tutor, e.g. Russell and Anne

## JOIN Expressions - INNER

- Find all matching tuples from two tables:

```SQL
SELECT * FROM tutor INNER JOIN tutee
ON tutor.tutor_id = tutee.tutor_id ORDER BY tutor.tutor_id;
```

![[Untitled 4 27.png|Untitled 4 27.png]]

- In the JOIN above, tutor is the left table, and tutee is the right table

![[Untitled 5 27.png|Untitled 5 27.png]]

## JOIN Expressions - LEFT OUTER

- Find all matching tuples and those that do not have a match from the left table:

```SQL
SELECT * FROM tutor LEFT OUTER JOIN tutee
ON tutor.tutor_id = tutee.tutor_id ORDER BY tutor.tutor_id;
```

![[Untitled 6 22.png|Untitled 6 22.png]]

- Note that LEFT OUTER and LEFT is the same

![[Untitled 7 21.png|Untitled 7 21.png]]

## JOIN Expressions - RIGHT OUTER

- Find all matching tuples and those that do not have a match from the right table:

```SQL
SELECT * FROM tutor RIGHT OUTER JOIN tutee
ON tutor.tutor_id = tutee.tutor_id ORDER BY tutor.tutor_id;
```

![[Untitled 8 20.png|Untitled 8 20.png]]

- Note that RIGHT OUTER and RIGHT is the same

![[Untitled 9 19.png|Untitled 9 19.png]]

## JOIN Expressions - FULL (OUTER)

- Find all matching tuples and those that have no match from both left and right tables

```SQL
SELECT * FROM tutor FULL JOIN tutee
ON tutor.tutor_id = tutee.tutor_id ORDER BY tutor.tutor_id;
```

![[Untitled 10 18.png|Untitled 10 18.png]]

- Combines RIGHT and LEFT OUTER JOIN

![[Untitled 11 16.png|Untitled 11 16.png]]

## JOIN Expressions - General Form

- Given all four types of JOIN, one can use the following syntax:

```SQL
SELECT column1, column2..
FROM left_table
type JOIN right_table
ON (matching criterion)
WHERE condition1, condition2 ..
ORDER BY value
```

![[Untitled 12 15.png|Untitled 12 15.png]]

## Lossless Joins

![[Untitled 13 13.png|Untitled 13 13.png]]

Lossy join decomposition — integrity lost with name as superkey!

FD name → person_id, street, city, salary

Lossless join decomposition — integrity kept (superkey person_id)

FD person_id → name, street, city, salary

# Functional Dependencies

## It’s all about the keys!

- JOIN combines data from different relations to return all necessary data
- Joining criteria (relationships) are based on primary & foreign keys
- We need to apply some theory to help us identify:
    1. Superkeys of a relation
    2. Whether it is OK to decompose it into smaller relations
        - ensuring the recreation of the original relation through `JOIN`
        - evaluating the decomposed schema

## Functional Dependencies

- A functional dependency (FD) is an integral part of the relational model — a form of constraint
- FD: a → b ⇒ (t1[a] = t2[a] ⇒ t1[b] = t2[b])
    - Determinant `a` functionality determines dependent `b`
    - If two tuples t1 and t2 agree on the `a` attribute, then they must also agree on the `b` attribute too

![[Untitled 14 13.png|Untitled 14 13.png]]

## Determining Functional Dependencies

- FDs ensure data integrity and no data redundancy in a database
- For any relation, the initial set of FDs are given by the project specification (common sense, experience and business-related)
- Further FDs can then be inferred by applying axioms & rules
- In general, we aim to have fully functional dependencies and eliminate partial and transitive dependencies as they cause design anomalies

## Fully Functional Dependency

- Definition: FD X → Y is a fully functional dependency if Y is full functionally dependent on X, but not on any proper subset of X
- {supplier_id, item_id} → price

![[Untitled 15 10.png|Untitled 15 10.png]]

## Partial Dependency

- Definition: FD X → Y is a partial dependency if a Y is functionally dependent on X, and Y can be determined by a proper subset of X
- {student_id, project_id} → {student_name, project_title}

![[Untitled 16 9.png|Untitled 16 9.png]]

- BUT the student_name and project_title functionally depend on part of the candidate key {student_id, project_id}

## Transitive Dependency

- Definition: If FD A → B and B → C hold, then A → C (axiom of transitivity)
- {class} → {teacher_name}
- {teacher_name} → {teacher_age}
- {class} → {teacher_age} !!!

![[Untitled 17 9.png|Untitled 17 9.png]]

- With class being the candidate key, the non-key attribute teacher_age depend on the non-key attribute teacher_name

# Normal Forms (1NF to 3NF)

## What is normalisation?

- Normalisation is a set of criteria for eliminating redundant data and avoiding operation anomalies
- Become more restrictive as you go down the list:
    - 1NF: all tables are flat
    - 2NF: good enough
    - 3NF: most common
- Hierarchy is followed, e.g. if your schema complies with 3NF it should also comply with 2NF and 1NF

## First Normal Form (1NF)

- All types must have atomic domains
- No repeated groups

## Second Normal Form (2NF)

- All relations must comply with 1NF
- Non-key attribute must fully develop on the candidate keys

## Discussion on 2NF

- Given that all 1NF properties are met for a relation, if it has only simple candidate keys, this it is also 2NF
    - No PDs with simple candidate keys
- Building → postcode leads to anomalies
- Transitive dependency (TD): a non-key attribute determining a non-key attribute

## Third Normal Form (3NF)

- All relations must comply with 2NF
- No transitive functional dependencies are allowed

## Discussion

Normal forms solve different problems:

- 1NF: only atomic domains, no repeated groups
- 2NF: no partial functional dependencies
- 3NF: no transitive functional dependencies

Points to remember:

- Higher normal forms require more but smaller tables
- More tables can bring higher cost of maintenance
- It is important to meets the needs of applications