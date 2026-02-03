### Hadoop and DB: OLAP

 - OLTP (On-Line Transaction Processing) vs. OLAP (On-Line Analytical Processing)

![[Pasted image 20260203134010.png]]

 - Hadoop Underpinning OLAP
	 - Facilitate aggregation/analytical queries using SQL-like language instead of MapReduce aggregation program.
	 - Resolving ETL (Extract-Transform-Load) Bottleneck: ETL is often a slow nightly task, for which situations occur when 24-hour data takes longer than 24 hours for processing

![[Pasted image 20260203134130.png]]

### Hive Example: WordCounter

 - Hadoop is great for large-data processing!
	 - Java programming is horrible for data scientists
	 - Hive is attractive for those familiar with SQL

![[Pasted image 20260203134311.png]]

### Hive Example: Natural Join

 - Relational join on two tables in Hive
	 - Two tables of word counts from the Shakespeare collection and from the Bible respectively

![[Pasted image 20260203134357.png]]

### Hive

 - Hive: data warehousing application in Hadoop
	 - Developed by Facebook to cooperate with Cassandra (now HBase).
	 - Tables are stored on HDFS flat files + query execution is powered by MapReduce.
	 - High-level declarative query language is HiveQL, variant of SQL.

### Hive Architecture

![[Pasted image 20260203134553.png]]

### Metastore

 - Metastore
	 - Central repository of Hive metadata: Metastore Service + Backing Store.
	 - By default embedded metastore: metastore service (same JVM) + embedded Derby database (local disk).
	 - Local metastore: metastore service + standalone database.
	 - Remote metastore: metastore service (<=> Hive services) + standalone databases.

![[Pasted image 20260203134737.png]]

### HiveQL: Data Types

 - Hive Data Types
 
	 - Simple Type
	
	 ![[Pasted image 20260203134829.png]]
	 
	 - Collection Type
	 
![[Pasted image 20260203134843.png]]

### HiveQL: Database and Table

 - CREATE TABLE statement has quasi-semi syntax as in SQL

![[Pasted image 20260203134948.png]]
![[Pasted image 20260203134959.png]]

 - Managed Table vs. External Table
	 - Managed Table: Hive manages the content of the table, data is stored in Hive warehouse directory.
	 - External Table: Hive does not move the data into warehouse directory, nor check its existence.

### Hive Storage: Text Encodings

 - Plain Delimited Text (Default) vs. JSON format

![[Pasted image 20260203140150.png]]

![[Pasted image 20260203140210.png]]

### Hive Storage: Binary Storage Formats

 - Binary Storage Formats
	 - Row-oriented: Sequence files (SequenceIFile in Hadoop), Avro datafiles.
	 - Column-oriented: RCFile (Record Columnar File) -> ORCFile (Optimised RCFile), Parquet (Cloudera)
 - Schema on Read vs. Schema on Write
	 - RDB: schema on write - a table's schema is enforced at data load time.
	 - Hive: schema on read - the data schema is verified when issuing queries yet not loading data.


![[Pasted image 20260203140331.png]]

### HiveQL: Partition and Buckets

 - Database
	 - Database as Hive warehouse directory: namespace/catalogue of tables
 - Table
	 - Each table is a unique directory under the database directory in HDFS.
	 - Table content as flat text files under table subdirectory.
 - Partition
	 - Allows for query efficiency on data slices, e.g., grid partition of taxi O/D data
	 - Partition is a nested subdirectory under the table directory.
 - Bucket
	 - For even better efficiency for query as well as sampling
	 - Bucket is a file under the table or partition directory

![[Pasted image 20260203154120.png]]
![[Pasted image 20260203154156.png]]

### HiveQL: Load/Import Data; Drop Table

![[Pasted image 20260203154218.png]]

### HiveQL: JOIN

 - Hive Supports all kinds of join operators

![[Pasted image 20260203154249.png]]

### HiveQL: Functions

 - Mathematical Functions
	 - ROUND(d)
	 - FLOOR(d)
	 - CEIL(d)
	 - RAND(d)
	 - etc
 - Aggregate Functions
	 - COUNT(expr)
	 - SUM(col)
	 - AVG(col)
	 - MIN(col)
 - Table Generating Functions
	 - EXPLODE(array)
	 - EXPLODE(map)
 - Other Built-in Functions
	 - String Functions
	 - Date Functions
	 - Collection utility functions
 - User-Defined Functions (UDF)
	 - User Defined Function
	 - User Defined Aggregate Function
	 - User Defined Table Function

![[Pasted image 20260203154437.png]]![[Pasted image 20260203154445.png]]
![[Pasted image 20260203154616.png]]

### WordCount Revisited

![[Pasted image 20260203154633.png]]
![[Pasted image 20260203154641.png]]