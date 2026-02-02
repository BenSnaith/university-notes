### What is Hadoop?

 - Hadoop is a software platform composed of:
	 - **HDFS** - Hadoop distributed file system.
	 - **MapReduce** - Offline distributed / parallel computing engine.
 - Hadoop targets at parallel running of data-intensive applications on clusters of the order of 10K+ nodes based on HDFS + MapReduce
	 - MapReduce divides applications into many small blocks of work.
	 - HDFS creates multiple replicas of data blocks that many fit application blocks.
	 - MapReduce can then processes data where it is located (more computation to data - data parallelism).

![[Pasted image 20260202102751.png]]

### Hadoop Architecture: Logical

 - Hadoop is designed as a **master-slave** **shared-nothing** architecture
	 - Big data is stored in Hadoop Distributed File System (HDFS)
	 - Big data is processes in Parallel using MapReduce.

![[Pasted image 20260202102946.png]]

### Hadoop Architecture: Physical

![[Pasted image 20260202103020.png]]

### Hadoop Users

 - Hadoop @ Yahoo
 - Yahoo's Hadoop cluster sorted 1 terabyte of data in 209 seconds, which bears the previous 297-seconds record (July 2008)
	 - Annual general prupose (Daytona) terabyte sort benchmark.
		 - 10 billion 100 byte records, completely sorted and written to disks
	 - The cluster has 910 nodes
		 - 2 quad core Xeons @ 2.0ghz per node.
		 - 4 SATA disks per node; 8G RAM per node.
		 - 1 gigabit Ethernet on each node.
		 - 40 nodes per rack.
		 - 8 gigabit Ethernet uplinks from each rack to the core.
		 - Red Hat Enterprise Linux Server Release 5.1 (kernel 2.6.18)
		 - Sun Java JDK 1.6.0_05-b13
	 - The sort used 1800 Maps and 1800 Reduces and allocated enough memory to buffers to hold the intermediate data in memory.
 - Hadoop @ Facebook
	 - Started in 2009; 320 machine cluster with 2560 cores and about 1.3PB raw storage.
	 - To store copies of internal log and use it as a source for reporting/analytics and machine learning.
 - Hadoop @ Baidu
	 - For a variety of Baidu tasks
		 - To store Web search logs and make statistical analysis.
		 - To analyse user behaviour and user relationships.
		 - To cluster and recommended Web pages.
	 - Started in 2008: 2 clusters with 300 machines
	 - 2015: 20000+ machines with largest cluster of 4000+ nodes
		 - 20PB+ data processed every day.
		 - 120000+ jobs executed every day.

### Hadoop Ecosystem

 - HDFS: distributed data storage system.
 - MapReduce: distributed data processing framework.
 - HBase: distributed column-oriented open-source database.
 - Hive: open-source data warehouse based on Hadoop supported by MapReduce.
 - Pig: High-level programming framework for MapReduce based data processing.
 - Common: supportive packages, including FileSystem, RPC, and serialisation, etc.
 - Avro: schema-based data serialisation tool.
 - Sqoop: data transferring tool between relational databases and Hadoop file system.
 - Flume: log data manager.
 - Chukwa: log data processing system for monitoring and analysing distributed system.
 - ZooKeeper: task coordinator.

![[Pasted image 20260202104229.png]]

### Distributed File System Design

 - A preliminary design
	 - Fault-tolerant high availability
	 - Low throughput

![[Pasted image 20260202104322.png]]

 - A more Robust and Efficient Design
	 - Basic functionalities fulfilled yet not enough details

![[Pasted image 20260202104404.png]]

### Google File System: Motivation

 - Google's Motivation in Early 2000s
	 - Crawls and stores copies of the whole Web on cheap commercial PCs
		 - Store it all on "one big disk".
		 - Process users' searches on "one big CPU".
	 - Google's Facts in Early 200s
		 - Google stores dozens of copies of the entire Web.
		 - Thousands of queries served per second.
		 - One query reads 100's of MB of data and 10's of billions of CPU cycles.
		 - Customised parallel supercomputer: expensive.
 - Google needs a large, distributed, highly fault-tolerant file system.
	 - Component failures normal: clustered computing on cheap commercial PCs.
	 - Files are huge (multi-GB): unwieldly to handle may small files.
	 - Most files are mutated: No random access or overwrite.

### Google File System: Design

 - GFS Design Decisions
	 - Files stored as chunks at multiple chunkservers: Fixed size (64MB)
	 - Single **master** to coordinate access and keep metadata
		 - Centralised management: chunkserver states via periodic heartbeats
	 - Reliability through replication: 3+ chunkservers
	 - No data caching: streaming reads of large data sets.
	 - Familiar interface with customised API: focus on Google apps.

![[Pasted image 20260202110139.png]]

### HDFS: Hadoop Distributed File System

 - HDFS is an open-source clone of Google File System
	 - Creates multiple replicas of data blocks for reliability and availability.
	 - Places data blocks on computing nodes and parallel processing.

![[Pasted image 20260202110249.png]]

### Block

 - File is split into fix-sized large blocks.
	 - Default block size 64MB/128MB, configurable - **logical** block.
		 - More time for data transmission rather than disk seek.
	 - File smaller than 64MB/128MB saved in a single block, yet not occupying this size of disk space.
	 - Cost of disk seeks is minimised due to large block size.
	 - Block is an abstraction for extremely large files.
	 - Block is a simplification for system design
		 - Block is fixed size -> data management simplified.
		 - Block equals to chunk -> metadata separated from block.
	 - Block fits well with fault tolerance and high availability
		 - A file is replicated with each block replicated in several nodes

![[Pasted image 20260202204349.png]]

### NameNode

 - (Active) NameNode
	 - Daemon program of HDFS (**master**), one per cluster.
	 - Manages the filesystem namespace
		 - Namespace image (fsimage) and edit logs (fsedits)
		 - Files and directories in the filesystem tree and their metadata.
	 - Maintains block information
		 - Bloccks of files and block replicas locations on different datanodes
		 - Retrieved from datanodes at system startup
	 - Configures replication strategies
	 - Coordinates client requests of read/write operations
	 - The single point of failure for the HDFS cluster.
		 - Replicas of namenode files.
	 - Hadoop 3
		 - Could have more name nodes in a cluster.

![[Pasted image 20260202204927.png]]

### Secondary NameNode

 - Secondary/Standby Namenode
	 - Assistive backend program for monitoring HDFS status, one per cluster.
	 - Periodically merges namespace image and edit log.
	 - Runs on separate physical machine from active namenode.
	 - Serves as an alternative namenode in the event of the failure of the primary.

### DataNode

 - DataNode
	 - One for each **slave** server.
	 - The chunkserver (as in Google's GFS paper) for storing block replicas of HDFS files.
	 - The worker (as in Google's Map-Reduce paper) for executing Map/Reduce tasks using either local blocks or nearly blocks.
	 - In responsibility of reading and writing data blocks from and into its local file system.
	 - Periodically reporting to namenode the list of blocks on it.
 - Client
	 - Split files into blocks.
	 - Retrieves file blocks and block locations from namenode.
	 - Asks datanodes to perform block-wise reading or writing of data.

### Performance Issues

 - Replication factor
 - Replica placement strategy
	 - Replica 1: the same node of the writing client.
	 - Replica 2: a random node in a different (remote) rack.
	 - Replica 3: another node in the same remote rack.
	 - Other replicas: picked randomly (HDFS stores 3 replicas by default)
 - Limitation: HDFS is not good at storing small files
	 - Metadata stored in main memory of NameNode
		 - Number of files/blocks limited by namenode capacity.
		 - 150B memory for metadata for one small file which accounts for a block.
		 - 100M blocks take up ~20GB memory vs. 100M small files take up only (less than) 1TB.
	 - Long disk seek time for large amount of small files
		 - Copying 10 100MB files vs. 10000 100KB files

