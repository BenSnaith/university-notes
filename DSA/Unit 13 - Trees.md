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
- __A binary tree:__ a tree with order 2 (i.e. a 2-ary tree)

An empty tree has a size of 0.

- __The height of a tree:__ 
	1. the number of nodes on the _longest_ path from the root to a leaf.
	2. the number of connections (aka edges or arcs) along the _longest_ path from the root to a leaf.
	(sometimes called the _depth_ of the tree)
- __The sub-tree rooted at a node__ is a tree consisting of the node itself plus all of its descendants.
- __The size of a tree/sub-tree__ is the number of nodes that it contains.

### Implementing Binary Trees

- The most obvious implementation of _tree_ ADT is using _non-linear, hierarchical linked structure_ or _tree_ for short!

	_Note: trees can be implemented using arrays (like a heap)_

### Implementing Binary Trees

- The fundamental building block of a binary tree is a linked node with two _follower nodes_: `left` and `right`.

	_Note: each linked node also references one element._

- A _binary tree_ can be created by putting the linked nodes together:

![[Pasted image 20241213170101.png]]

### Implementing Binary Trees

- For a _binary tree_ itself, we define a _generic `BinaryTree`_ object with a `protected` field `root` representing the `root` of the tree.

```java
public class BinaryTree<T> implements Iterable<T> {
	protected BinaryTreeNode<T> root;

	// Other methods omitted for the moment.

	protected static class BinaryTreeNode<E> {
		// Inner class for BinaryTreeNode
	}
}
```

- `root` is of the _static inner_ type `BinaryTreeNode`.

### Spot the difference: Static vs. non-static inner classes.

```java
public class BinaryTree<T> implements Iterable<T> {

	// other details omitted.

	protected class BinaryTreeNode {
		private T element;
		private BinaryTreeNode<T> left;
		private BinaryTreeNode<T> right;

		public BinaryTreeNode(T element) {
			this.element = element;
			left = null;
			right = null;
		}

		public boolean isLeft() {
			return (left == null && right == null);
		}
	}
}
```

vs.

```java
public class BinaryTree<T> implements Iterable<T> {

	// other details omitted.

	protected static class BinaryTreeNode<E> {
		private E element;
		private BinaryTreeNode<E> left;
		private BinaryTreeNode<E> right;

		public BinaryTreeNode(E element) {
			this.element = element;
			left = null;
			right = null;
		}

		public boolean isLeft() {
			return (left == null && right == null);
		}
	}
}
```

### Inner Class `BinaryTreeNode`

- All tree nodes of a __binary tree__ will be instances of `BinaryTreeNode`.

- Each node holds a reference to the _element_ stored in that node and references to the _two possible children_ of the node.

### Trees & Recursion

- For tree processing, _recursive algorithms_ are natural and virtually essential.
- Consider the coding of the `size` and `height`.
	- Iterative approaches are usually very clumsy and error prone.
- __Two__ different implementations:
	1. Using a _non-recursive wrapper method_ and a _recursive method_ which takes a parameter of type `BinaryTreeNode`.
	2. Using a recursive method in the inner class `BinaryTreeNode`.

### Methods `size` & `height`

```java
	public int size() {
		return size(root);
	}

	protected int size(BinaryTreeNode<T> node) {
		if(node == null)
			return 0;
		else
			return 1 + size(node.left) + size(node.right);
	}

	public int height() {
		return height(root);
	}

	protected int height(BinaryTreeNode<T> node) {
		if(node == null)
			return 0;
		else
			return 1 + Math.max(height(node.left), height(node.right));
	}
```

`max` is a `static` method from class `java.lang.Math`.

### Tree Traversal (1)

- _Tree-traversal_ refers to the process of _visiting_ (examining and/or updating) _each node_ in a tree data structure in a systematic way.
- Tree traversals are classified by the _order_ in which nodes are _visited_.
- To traverse a _non-empty_ binary tree, perform the following operations recursively, starting at the root:
	- _pre-order traversal_ or depth-first traversal:
		1. Visit the root.
		2. Traverse the left sub-tree.
		3. Traverse the right sub-tree.
	- _in-order traversal_ or symmetric traversal:
		1. Traverse the left sub-tree.
		2. Visit the root.
		3. Traverse the right sub-tree.
	- _post-order traversal_:
		1. Traverse the left sub-tree.
		2. Traverse the right sub-tree.
		3. Visit the root.
	- _level-order traversal (breadth-first)_
		- Visit every node on a layer at a time. (likely using a Queue).

- For all types of traversal, there also exists a _reverse_ traversal of the same kind (where the roles of the left and right are reversed)

	_Literally just flip them around in the code..._

- Which kind of traversal is appropriate depends on the _nature_ of the data stored in the ree, and the purpose it is being used for.

### A `toString` method for trees using in-order traversal

```java
@Override
public String toString() {
	StringBuilder result = "{ ";
	result += toString(root);
	result += " }"
	return result.toString();
}

protected String toString(BinaryTreeNode<T> node) {
	if(node == null)
		return "";
	else
		return toString(node.left) + " "
			   + node.element.toString() + " "
			   + toString(node.right);
}
```

For __pre-order__ or __post-order__ versions and their reversed variants, simply _alter the order_ of calls to the various `toString` methods in `return`command for the recursive case.

### A `copy` method for trees using pre-order traversal

- Copying a tree recursively is particularly elegant.

- Using _pre-order traversal_, we copy the root node and then 'hang' copies of the left and right sub-trees from it.

```java
public BinaryTree<T> copy() {
	BinaryTree<T> result = new BinaryTree<>();
	result.root = copy(root);
	return result;
}

protected BinaryTreeNode<T> copy(BinaryTreeNode<T> node) {
	if(node == null)
		return null;
	else 
		return new BinaryTreeNode<T>(node.element,
									 copy(node.left),
									 copy(node.right));
}
```

### Level-Order Traversal

- Level-order traversal can be implemented using a simple iterative algorithm with a FIFO Queue of nodes.
- We start by enqueueing the root node, then we enter a loop which terminates when the Queue becomes empty.
- In the loop, we dequeue a node (this is the node currently being visited) and enqueue its (non-null children).

```java
public void levelOrderPrint() {
	QueueADT<BinaryTreeNode<T>> nodes = new LinkedQueue<>();

	BinaryTreeNode<T> node;

	if (root != null) nodes.enqueue(root);

	while(!nodes.isEmpty()) {
		node = nodes.dequeue();
		System.out.println(node.element.toString() + " ");
		if(node.left != null) nodes.enqueue(node.left);
		if(node.right != null) nodes.enqueue(node.right);
	}
}
```

### A `find` method

- We can use any method of traversal to find an element in a tree, e.g. _depth-first_ (pre-order) of _breath-first_ (level-order) search.
- We use __pre-order traversal__ here.
- We terminate the traversal as soon as we find the required item.

```java
public T find(T target) {
	BinaryTreeNode<T> tmp = find(target, root);
	if(tmp == null) return null;
	else return tmp.element;
}

protected BinaryTreeNode<T> find(T target, BinaryTreeNode<T> node) {
	if(node == null)
		return null;
	else if(target.equals(node.element)) 
		return node;

	BinaryTreeNode<T> tmp = find(target, node.left);
	if(tmp == null)
		tmp = find(target, node.right);
	return tmp;
}
```

### Tree Iterators

- The simplest way to implement an __iterator__ is to place the elements into a _temporary list_ and iterate over this list.
- The example below uses _in-order_.

	_We may use any method of traversal as we fill the list._

- For simplicity, this iterator will not support `remove`.

```java
public Iterator<T> iterator() {
	ArrayList<T> list = new ArrayList<>();
	inorder(root, list);
	return list.iterator();
}

protected void inorder(BinaryTreeNode<T> node, ArrayList<T> list) {
	if(node != null) {
		inorder(node.left, list);
		list.add(node.element);
		inorder(node.right, list);
	}
}
```

### Adding Elements

- We could define methods:
	- `addLeft(T parent, T child)`
	- `addRight(T parent, T child)`
- These would:
	1. Search for the node containing the `parent` (using the `protected` method `find`)
	2. Add a new node containing `child` as _either_ the left or right child respectively.
- `IllegalStateExeception` may be thrown anywhere:
	- the `parent` was not found; or
	- the `parent` already has a left/right child.

Depending on the application, the specified element can replace an existing child.

### Removing Elements

- We could also define methods:
	- `removeLeftChild(T parent)`
	- `removeRightChild(T parent)`
- These would:
	1. Search for the node containing the `parent`.
	2. If the __child__ to be removed is a _leaf node_, simply set the appropriate left or right link in the parent to be `null`.
	3. If the __child__ to be removed _has descendants_ we could:
		- remove the child and _all_ is descendants by setting the link to `null`
		- if the child itself has _one one_ child, make this 'grandchild' the child of the patient.
		- if the child has _two_ children, throw an __exception__, OR
		- use some more advanced method appropriate to the situation.

### Removing Elements: Examples

- Remove `Jack`: simply set the right child of __Hope__ to `null`
- Remove `Bob`: simply remove the entire __sub-tree__ headed by __Bob__, _if_ it meets the underlying application's requirements.
- Remove `Ed`: simply name __Jill__ become the right child of __Bob__
- Remove `Guy`: simply throw an __exception__

![[Pasted image 20241214002114.png]]

### Balanced Trees

- A __perfect n-ary tree__ is a tree in which all leaf nodes have the same depth and all other nodes that have exactly `n` children.
- In particular, a __perfect binary tree__ of height `h` has 2^h-1 nodes
- A __Balanced n-ary tree__ is an n-ary tree which is perfect, or which becomes perfect if the deepest level is removed.
- The __depths__ of all leaf nodes in a balanced tree differ by at most 1.
- A balanced tree has the lowest possible overall _height_ for a tree of its size.
- A __balanced tree__ of height `h` has between 2^h-1 and 2^h - 1 elements.

### Balanced and Unbalanced Ternary Trees

![[Pasted image 20241214002927.png]]

A __balanced n-ary tree__ is an n-ary tree which is perfect, or which becomes perfect if the deepest level is removed.

### Binary Search Trees

- A __Binary Search Tree (BST)__ is a _binary tree_ with the added property:
	- all members of the _left sub-tree_ of __any__ node should _precede_ the parent node, and
	- all members of the _right sub-tree_ of __any__ node should _appear after_ the parent node.
- Organising data in a BST make searching more efficient...
	- A balanced BST will result in O(logn) search times.

### An extremely unbalanced BST

![[Pasted image 20241214003535.png]]

- A tree in which every node (except the leaf node) has one child is said to be _degenerate_.
	- Such a tree is equivalent to an __ordered list__ and searching in O(n).
- If a BST becomes very unbalanced, _re-balancing_ is needed to maintain search efficiency.

### Implementing a Binary Search Tree 

- We extended class `BinaryTree`, but we must constrain the type parameter so that we can make sure that we can compare elements.
- We introduce a `size` field so that we can override the inherited `size` with a simple efficient version.

```java
public class BST<T extends Comparable<T>> extends BinaryTree {
	private int size;

	public BST() {
		super();
		size = 0;
	}

	public BST(T elem) {
		super(elem);
		size = 1;
	}

	public int size() {
		return this.size;
	}

	// Other methods omitted.

}
```

### Adding elements to a BST using Recursion

- We compare the element to be added with the element in the root, depending on whether it should _precede_, or _follow_, the root element, we recurs to add it to the left or right sub-tree.
- The base case occurs when the node is `null`, a _new node_ containing the element is created and returned.
- If the item is already in the tree, we may either:
	- return without modifying the tree -> an unordered set; or...
	- add the _duplicate element_ either _before_ the existing element (in the left sub-tree) or _after_ (in the right sub-tree). 

### The method `add`

When the element is already present, add it _after_ the existing element

```java
public void add(T elem) {
	root = add(elem, root);
	size++;
}

protected BinaryTreeNode<T> add(T elem, BinaryTreeNode<T> node) {
	if(node == null) {
	
	}
}
```