### WordCounter: Simple

 - A Java programmer with good programming habits.

![[Pasted image 20260202210543.png]]

### WordCounter: Multiple Instances

 - Multi-thread
 - Lock on shared thread

![[Pasted image 20260202210618.png]]

### WordCounter: Improved

 - A multi-threaded word counter with separate parsers/counters.

![[Pasted image 20260202210700.png]]

### WordCounter: Peta-Scale

 - Manage large-scale distributed data.

![[Pasted image 20260202210728.png]]

### WordCounter: Divide & Conquer

![[Pasted image 20260202210803.png]]

### MapReduce: Basic

 - MapReduce is a parallel divide-and-conquer programming model
	 - Automatic parallelism + distributed data storage/processing.
	 - Programmers only care about the application logic, without considering the messy details of the underlying implementation.

![[Pasted image 20260202210906.png]]

### MapReduce: Combine

 - At the mapper side, a **combiner** is a pre-reducer for reducing part of the map outputs so that less intermediate data will be sent to the reducer.

![[Pasted image 20260202210951.png]]

### All-In-All: Single Reducer

![[Pasted image 20260202211011.png]]

### All-In-All: Multiple Reducers

 - Annually Highest Temperature: One output/reducer per year.

![[Pasted image 20260202211058.png]]

### Shuffle: Map Side

 - Circular buffer for IO efficiency of writing map outputs
	 - 100MB by default; adjustable.
	 - Spill buffer to disk when threshold (80% by default; adjustable) is reached.
 - Spill files are partitioned and sorted on key.
	 - Several intermediate spill files before the map phase finishes.
	 - Partitions of spill files are merged on disk as the final step of the map phase.
	 - Partitions available to be fetched by reducers via HTTP.

![[Pasted image 20260203123405.png]]

### Shuffle: Reduce Slice

 - Fetch partitions from all the related map task nodes.
	 - Asynchronous copying by periodically asking JobTracker for the locations of map outputs.
 - Partition data are merged, sorted and saved on local disks.
	 - Fetched partitioned data is copied to in-memory buffer.
	 - Partitions from different maps are merged and spilled to disk either if the buffer becomes too full or a certain number of partitions have been fetched.
	 - On-disk copies are merged into larger sorted files in several rounds in several rounds controlled by merge factor.

![[Pasted image 20260203123640.png]]

### Task Execution

 - All reducers start only after all the mappers complete.
 - **Straggler**: A mapper or reducer that takes a long time.
	 - Hardware degradation, software mis-configuration, bugs, etc.
 - Speculative Execution
	 - JobTracker speculates a slow-running task: much slower than average execution time.
	 - JobTracker launches an equivalent backup task, called speculative task, after detecting some stragglers.

![[Pasted image 20260203123906.png]]

### MapReduce: 1.0 Architecture

 - Hadoop is designed as a master-slave shared-nothing architecture.
	 - Big Data is stored in Hadoop Distributed File System (HDFS).
	 - Big Data is processed in Parallel using MapReduce.

![[Pasted image 20260203124105.png]]

### From MapReduce (1.0) to YARN

 - MapReduce 1.0 Problems:
	 - JobTracker as the performance bottleneck: execution + resource.
	 - Single-point failure of JobTracker.
	 - MapReduce as the only supported computing framework.
 - Resource Utility:
	 - Unbalanced resource utilisation of different computing frameworks in the same cluster.
	 - YARN as the generalised intermediate layer for resource scheduling: Yet Another Resource Negotiator.

![[Pasted image 20260203124324.png]]

### YARN: Architecture

![[Pasted image 20260203124340.png]]

### MapReduce with Shuffle

 - Map Phase: $map(k_1, v_1) -> list(k_2, v_2)$ or $list(k_2, list(v_2))$

	w Combiner            wo Combiner

 - Reduce Phase: $reduce(k_2, list(v_2)) -> list(k_3, v_3)$

![[Pasted image 20260203124622.png]]

### MapReduce Classes

 - Class 1: Map-Only MapReduce
	 - Without reduce phase: Map-Side Join.
 - Class 2: Classical MapReduce
	 - One round of Map and Reduce phases from input to output: WordCounter.
 - Class 3: Iterative MapReduce
	 - Several rounds with Reduce output fed back to Map input.
 - Class 4: Dependent MapReduce
	 - MapReduce joins with complex dependencies between each other (JobControl).
 - Class 5: Chaining MapReduce
	 - Several Map tasks combined into a data processing pipeline.

![[Pasted image 20260203124750.png]]
![[Pasted image 20260203124856.png]]

### MapReduce Chaining

 - ChainMapper/ChainReducer
	 - One or more Mappers (Map tasks) in the Map phase - ChainMapper.
	 - (Optionally) One or more Mappers (Map tasks) in the Reduce phase - ChainReducer.
	 - Only one Reducer (Reduce task) in the Reduce phase - ChainReducer.

![[Pasted image 20260203125031.png]]