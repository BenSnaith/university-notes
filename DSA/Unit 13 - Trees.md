### Unit Objectives 

- Learn about the TreeADT
- Learn the basic terminology for trees.
- Learn when to use trees.
- Explore the fundamental ideas on how to implement a TreeADT using a linked structure.
- Describe the time implications of searching an element in a tree.
- Consider some tree implementations of ADTs in the JCF.

### The TreeADT

Tree is a _non-linear, hierarchical_ structure.

A Tree has a set of _nodes_ that are connected as follows:

- Apart from the __root node__ (which has not parent), each node in a tree has exactly one parent.
- Each node in the tree points to >= 0 child nodes that are directly beneath it in the tree.

### Some Typical Tree Operations

- Enumerating all the items.
- Searching for an items.
- Adding a new item at a certain position on the tree.
- Deleting an item.
- Removing a sub-tree of a tree (i.e., pruning)
- Adding a sub-tree to a tree (i.e., grafting)
- Finding the root for any node.

### Some Common uses for Trees

- GUI Components.
- Chapters, Sections and Subsections in a book.
- Contents of a file system.
- Elements in an HTML document.
- Document Object Model (DOM).
- An XML Document.

### Modelling a Drop-down Menu

![[Pasted image 20241213130608.png]]

### Modelling a Window and its contents

![[Pasted image 20241213130647.png]]

### Modelling a Trie

A __Trie__ may be used to represent a dictionary of words:

- Valid places for word _endings_ are indicated by `*`
- Examples: `ale`, `an`, `and`, `ant`, `beet`
- For a language dictionary of 10,000 word entries, the look up time may be considered as O(1) as the length of each word is typically <= 35

![[Pasted image 20241213130943.png]]

### An Example of a Binary Search Tree

![[Pasted image 20241213131331.png]]

### Tree Terminology

- __Node:__ A location in the tree where an element is stored.
- __Empty Tree:__ A tree with no nodes.
- __Root:__ The node that is at the _base_ of the tree and so has _no_ parent
- __Child:__ A node that is _directly beneath_ another node in the tree.
- __Grandchild:__ A child of a child, etc.
- __Leaf:__ A node that does _not_ have any children.
- __Internal Node:__ A node that is not the root _and_ has at least one child.
- __Descendant:__ Given a node, a descendent is any node below another node and on a path from that node.
- __Ancestors:__ Given a node, an ancestor is _any_ node above another node on a connecting path from the root to that node.
- __Siblings:__ Children on the _same_ node.

### Extra Terminology

- __The depth of the node:__ the number of nodes on the path from the root to the node. This is sometimes called the _level of the node within a tree_.
- __A level of the tree:__ a set of all nodes at a given depth.
- __The order of the tree:__ the maximum number of children per node.
- __An n-ary tree:__ a tree with order n (all nodes have at most n children)
- __A binary tree:__ a tree with order 2 (i.e. )