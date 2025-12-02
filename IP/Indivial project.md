P2P

3rd Oct: Read up on DHT, P2P (Napster, Kademilia, Bittorrent, P2P Chat, Bitchat/Dorsey)
10th Oct: Find repositories of implementations of DHTs - Kademilia
1st Nov: Literature review straight into report
7th Nov: Customise a P2P for a given scenario or set up a large(ish) testbed to test scalability
Dec + Jan: Coursework + Exams

![[Pasted image 20250926114726.png]]
:w

Literature Review
Ben Snaith
This literature review examines the architectural differences between three of the most
influential DHT systems, highlighting similarities, differences and their lasting impact
on distributed systems research.
Chord: Ring-Based Routing with Consistent Hashing
Stoica et al. Introduced Chord in 2001 as a scalable P2P lookup protocol which address
the problem of locating data items in a distributed system.
Chord organises nodes into a ring topology using consistent hashing. Both nodes and
keys are assigned m-bit identifiers by hashing their IP addresses and data keys
respectively, mapping them onto a circular identifier space.
Chord’s core innovation is its finger table routing structure. Each node maintains a
finger table with m entries, m being the size of the identifier space in bits (i.e. if m = 8 the
identifier space would be 2 ^ 8 = 256), where the i-th entry points to the first node that
succeeds the current node by at least 2^(i-1) positions on the ring. This exponential
spacing enables Chord to achieve O(log N) lookup complexity, where N represents the
number of nodes in the system.
When performing a lookup, a node forwards the query to the node in its finger table
whose identifier most immediately precedes the target key. This process continues
iteratively or recursively until the query reaches the node responsible for the key.
Chord addresses node failures through successor lists, where each node maintains r
successors, where r is a value which can be defined to specify how many other nodes
are in each successor list and can be specified on a system-to-system basis. This
redundancy ensures that even if multiple consecutive nodes fail, the system can
remain operational, and the remaining nodes will become responsible for handling
those keys.
Pastry: Prefix-based Routing with Proximity
Rowstron and Druschel presented Pasty in 2001 as a scalable, self-organising
distributed object location and routing substrate. Pastry distinguished itself through its
incorporation of network proximity into routing decisions.
Similarly to Chord, Pastry assigns m-bit identifiers to nodes using consistent hashing.
However, Pastry’s routing is based on prefix matching rather than numerical distance.
Pastry maintains three data structures at each node: a routing table, a neighbourhood
set, and a leaf set. The routing table is organised into rows and columns, where row n
contains the entries for nodes whose identifiers share the first n digits with the current
node but differ in digit n+1. The leaf set contains the numerically closes nodes in each
direction in the identifier space, while the neighbourhood set contains m nodes that are
closest in terms of network proximity.
Routing proceeds by forwarding messages to a node that shared a longer common
prefix with the destination key, if no such node exists in the routing table, the message
is forwarded to nodes in the leaf set that a numerically closer to the key. This prefix-
based approach achieves O(log N) time complexity.
A distinguishing feature of Pasty is it exploitation of network locality, during table
construction, Pastry selects entries that are nearby in the underlying network topology,
this is usually measured using a metric like round-trip time, this helps to reduce latency
compared to other approaches
Pastry uses the leaf sets stored by each node in or to handle failures. When a node
detects a failed neighbour, it requests replacement information from other nodes.
Kademlia: XOR Metric and Parallel Lookups
Maymounkov and Mazières introduced Kademlia in 2002, presenting a peer-to-peer
information system with several novel features which distinguish it from earlier DHT
systems.
Each Kademlia node organises its view of the network into a binary tree structure with k-
buckets. The node’s own identifier defines the root of this tree, and each k-bucket
corresponds to a subtree covering a specific distance range from the node.
Kademlia’s routing algorithm performs iterative lookups by querying a nodes in parallel,
where a is typically 3. At each step, the initiator selects a closest nodes which its has
not yet queried and sends parallel requests, as responses arrive, the initiator updates
its view of the closest nodes and continues querying it until it has contacted the k
closes nodes or no closed nodes are being discovered. This parallel approach achieves
O(log N) routing complexity while providing robustness against individual node failures.
Kademlia introduces several innovative features, one being symmetric routing. The XOR
metric ensures that all node pairs agree on their mutual distance, simplyfing protocol
design and enabling more efficient routing table updates. Kademlia also preferentially
retains nodes that have been online longer in its k-buckets, based on the obersvation
that nodes with a longer uptime will likely remain online.
Kademlia’s failure mechanisms operate on multiple levels. The k-bucket structure
maintains multiple alternative paths to any given region of the identifier space. During
lookups, parallel queries ensure that a small number of node failures do not prevent
successful key resolution. Additionally, Kademlia implements a republishing
mechanism where key-value pairs are periodically republished to ensure availability
despite node churn.
General Comparison
All three systems achieve O(log N) lookup complexity but by different mechanisms.
Each system requires O(log N) state per node, this basically means the amount of
routing information needed to be stored by each node about other nodes in the
network.
Pastry is the only system which explicitly incorporates network proximity into routing
decisions.
Kademlia’s parallel lookup strategy provides the most roduct approach to handling
node failures during routing. A single failed node in the lookup path will not significantly
inpact query success as alternative paths can be explored simultaneously.
Kademlia’s XOR metric creates symmetric routing relationships – If A considers B close,
then B considers A equally close. This symmetry simplifies the routing table and
guarantees that communication paths are bidirectional. Contrastingly, Chord and
Pastry’s asymmetric distance metrics mean that the proximity my differ depending on
perspective.
Despite these differences, all three approaches have found practical adoption. Chord’s
simplicity have found it popular in academic research and teaching, acting as a good
first look into P2P systems and DHTs. Pastry has found itself being the foundation to
several storage systems and Kademlia has achieved the most significant practical
adoption, notably as the DHT underlying the BitTorrent distributed tracker protocol and
the Ethereum blockchain’s node discovery mechanism.
