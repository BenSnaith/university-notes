# Distributed Data Management

### Dealing with Data Volume

![[Pasted image 20260201111216.png]]

### Distributed Database System

 - Distributed System
	 - A distributed system is a system that runs on a collection of machines that do not have shared memory, yet looks to its users like a single computer.
 - Distributed Database System
	 - A distributed database (DDB) is defined as a collection of multiple, logically interrelated databases distributed over several sites in a computer network.
	 - A distributed database management system (DDBMS) is then defined as the software system that permits the management of the distributed database and makes the distribution transparent to the users.

### Distributed Data Storage Issues

 - Data Fragmentation
	 - Relation is partitioned into several fragments stored in distinct sites.
	 - A table is usually split into a number of small parts and each part is called a fragment of the original table.
	 - A fragment of a table will be stored onto different sites.
	 - Fragments contain sufficient information for a lossless conversion of the original table.
	 - Horizontal fragmentation and vertical fragmentation.

![[Pasted image 20260201111605.png]]

### Data Fragmentation: Horizontal

![[Pasted image 20260201112048.png]]

### Data Fragmentation: Vertical

![[Pasted image 20260201112038.png]]

### Data Fragmentation: Advantages

 - Horizontal:
	 - Allows parallel processing on (different rows of) fragmentation on a relation.
	 - Allows a relation to be split so that tuples are located where they are most frequently accessed.
 - Vertical
	 - Allows tuples to be split so that each part of the tuple is stored where it is most frequently accessed.
	 - Tuple-id attribute allows efficient joining of vertical fragments.
	 - Allows parallel processing on (different columns of) a relation.

### Mixture of Fragmentation

 - Vertical and Horizontal fragmentation can be mixed

![[Pasted image 20260201112437.png]]

### Distributed Data Storage Issues

 - Data Replication
	 - Multiple copies of data stored in different sites.
	 - For faster retrieval and fault tolerance.
- Combining Replication and Fragmentation
	- Relation is partitioned into several fragments.
	- System maintains several identical replicas of each such fragment.

![[Pasted image 20260201112548.png]]

### Data Replication

 - A relation or a fragment of a relation is replicated if it is stored redundantly in two or more sites.
	 - Full replication: a relation R is stored at all sites.
	 - Partial replication: a fragment of a relation R is replicated at some sites.
 - Advantages of Replication
	 - Availability: failure of site containing relation R does not result in unavailability of R is replicas exist.
	 - Parallelism: queries on R may be processes by several nodes in parallel.
	 - Reduced Data Transfer: relation R is available locally at each site containing a replica of R.
 - Disadvantages of Replication:
	 - Increased cost of updates: each replica of relation R must be updated.
	 - Increased the complexity of concurrent control: concurrent updates to distinct replicas may lead to inconsistent data unless special concurrency control mechanisms are implemented.
		 - Strong consistency vs. eventual consistency.
 - Synchronous Replication vs. Asynchronous Replication.

### Concurrency Control: Primary Copy

 - Concurrency Control: means an update must be reflected on all replicaes of data item, to keep data consistency across all sites.
 - Choose one replica of data item to be a primary copy.
	 - Primary Site of data item: site containing the replica.
	 - Different data items can have different primary sites.
	 - Lock occurs at primary site.

![[Pasted image 20260201113350.png]]

 - Pros and Cons
	 - Pros: Concurrency control for replicated data handled in a similar way to data that is not replicated - a simple implementation
	 - Cons: If the primary site of a data item fails, the data item is inaccessible even through other sites containing a replica may be accessible.

### Master-Slave Architecture

 - Master-Slave Replication:
	 - Updates are performed at single "master" site, propagated to "slave" sites.
	 - Data may only be read at slave sites, not updated.
		 - No need to obtain locks at any remote site.
	 - Propagation is not part of the update transaction: it is decoupled.
		 - May be immediately after transaction commits or may be periodic.
	 - Particularly useful for distributing information.
		 - e.g., from central office to branch-office.

### Concurrency Control: Quorum

 - $N$: The number of sites/nodes that store a replica of the data.
 - $W$: The minimum number of replicas that need to be updated before we can say a write operation competes - **write quorum**.
 - $R$: The minimum number of replicas that are to be contacted when a data item is accessed by a read operation - **read quorum**.
 - **Conditions: W + R > N; W > N / 2 (locks when reading / writing; replica version)**

![[Pasted image 20260201114107.png]]

### Concurrency Control: Weighted Quorum

A generalisation of Quorum

 - Each site is assigned a weight.
	 - Let $S$ be the total of all site weights
 - Choose two values **read quorum** $Q_r$ and **write quorum** $Q_w$/
	 - Such that $Q_r$ + $Q_w$ > $S$ and 2 * $Q_w$ > $S$.
	 - Quorums can be chosen (and $S$ computed) separately for each items.
 - Each read must lock enough replicas that the sum of the site weights is >= $Q_r$.
 - Each write must lock enough replicas that the sum of the site weights is >= $Q_w$.

### Concurrency Controls: Paxos

 - Paxos:
	 - Is an synchronous consesus based on messages which guarantees data consistency is distributed algorithmic system that can tolerate non-malicious failures.
	 - Is widely used in the industry, such as Google's Chubby and it's open souce implementation Apache, ZooKeeper, etc.
 - Three Roles is Basic Paxos (for each site):
	 - **Proposer**: proposes a new proposal for a new value $v$ with a proposal number $n$ to a majority set of acceptors for a vote. (~ politician)
		 - Proposal number $n$: A globally different number for each proposal for discrimination.
	 - **Acceptor**: receives a number of proposals and make decisions about whether to accept some proposals or to deny some other. (~ MP)
		 - Accept a proposal: if its number is larger then the highest number among the proposals that the acceptor has received and responded previously.
	 - **Learner**: learns a value once it has been chosen by a majority vote (~ citizens).
		 - Choose a value: if a proposer's proposal is accepted by the majority set of acceptors.

### Paxos: The Algorithm

 - Phase 1 (**prepare** request)
	 - (a) A proposer chooses a new proposal version number $n$, and sends a **prepare** request (**PREPARE**, $n$, $v$) to a majority set of acceptors:
		 - Can I make a proposal with number $n$?
		 - If yes, do you suggest some value for my proposal?
	 - (b) An acceptor responds to each received prepare request (**PREPARE**, $n$, $v$):
		 - If the proposal is the final proposal the acceptor meets, it sends out an acknowledgement message (**ACK**, $n$, $NIL$, $NIL$).
		 - If $n$ is greater than any prepare request it has already responded, it sends out an acknowledgement message (**ACK**, $n$, $n*$, $v*$) where $n*$ and $v*$ are the largest number and value among all the previous proposal respectively, with a promise not to accept any more proposals numbered less than $n$.
 - Phase 2 (**accept** request)
	 - Similar to the bill phase in the Political scenario.
	 - (a) If the proposer receives **POSITIVE** responses from all the acceptors in the majority set, it issues an **accept** request (**ACCEPT**, $n*$, $v*$), where
		 - $n*$ is the number that appears in the prepare request, and
		 - $v*$ is the value of the highest-numbered proposal among the responses.
	 - (b) When the acceptor receives an accept request (**ACCEPT**, $n*$, $v*$), it accepts to proposal unless it has already responded to a prepare request having a number greater than $n*$.
 - Phase 3 (**learning** phase)
	 - Acceptors notify learners of a determined proposal value if no conflicts occur.

### Paxos: Example 1

![[Pasted image 20260202102236.png]]

### Paxos: Example 2

![[Pasted image 20260202102253.png]]

### Paxos: Example 3

![[Pasted image 20260202102312.png]]![[Pasted image 20260202102323.png]]

### Paxos: Example 4

![[Pasted image 20260202102343.png]]