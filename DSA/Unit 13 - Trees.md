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
		return new BinaryTreeNode<T>(elem);
	}

	int comp = elem.compareTo(node.element);
	if(comp < 0) {
		node.left = add(elem, node.left);
	}
	else {
		node.right = add(elem, node.right)
	}
	return node;
}
```

### An efficient search method `find`

- By comparing the `target` element with the element in a node, we know whether to search its left or right sub-tree. (__Binary Search__)

```java
protected BinaryTreeNode<T> find(T target, BinaryTreeNode<T> node) {
	if(node == null)
		return null;

	int comp = target.compareTo(node.element);
	if(comp < 0)
		return find(target, node.left);
	else if(comp > 0)
		return find(target, node.right);
	else
		return node;
}
```

- Note that we do not need to override the inherited `public find` method, only the `protected` one.

### Removing a Specified Element

This operation is more _complicated_ than adding an element...

- First locate the node to be removed using `find`.
- If the node to be removed has children, then we cannot simply remove the node and 'orphan' its children.
- Instead, a node needs to be 'promoted' to replace the removed one as parent. This must be done in a way which maintains the correct ordering of elements.
- A helper method `promote` needs to be written:
	- If the node has _no_ children, `promote` returns _null_.
	- If the node has only _one_ child, `promote` returns that child.
	- If the node has _both_ children, `promote` returns the _left-most right successor_.
- To find the _left-most right successor_, we follow the right link of the node to be removed, then follow left-links as far as possible.
	- This node has no left child (otherwise it would not be the left most.)
- We replace the node to be removed by the _left-most right successor_
- If the _left-most right successor_ node has a right child, replace it by its right child.

### Time Complexity of Binary Search Tree Operations

- For all of the methods `add`, `find` and `remove`, the most expensive part of the operation is the search for the _correct position_ of the element (and for the _left-most right successor_). This has time complexity _O(log2n)_ if the tree is balanced or nearly so.
- The actual 'plumbing' to add or removed the node is O(1) and so the overall time complexity is still O(log2n) as this is the dominant term.

### Analysis of Trees

- Trees are a useful and efficient way to implement other collections. _e.g., class `TreeSet`, `TreeMap` in JCF_.
- _Each_ search requirements going along _one_ path from the _root_ to a _left._
- Thus, searches in BST can be programmed using either a __loop__ or __recursion__.
- The __height__ of a balanced tree will be less than _log2(n) + 1_, where _n_ is the number of elements in the tree.
- Using a _balanced_ binary search tree to implement an _ordered_ list, the `find` operation will execute in _logarithmic_ time (i.e. _O(logn)_)

### Linked List vs. Binary Search Tree

- An _ordered list_ can be implemented using a linear linked structure, and array or a binary search tree.
- Classes `java.util.TreeSet` and `java.util.TreeMap` in JCF are _two_ implementations of an _ordered list_ using a tree data structure.
- Analysis of _linked list_ and balanced _binary search tree_ implementations of an ordered list:

![[Pasted image 20241214135501.png]]

To ensure an _O(logn)_ performance, we need a _balanced_ binary search tree. In `size`, we assume the existence of a `size` field updated by add and remove operations.

- Each node in an N-ary can have N or fewer children.
	- Using the linked nodes alone to model the children is rather tedious and inflexible except perhaps for ternary trees:

```java
protected static class TernaryTreeNode<T> {
	private T element;
	private TernaryTreeNode<T> left;
	private TernaryTreeNode<T> center;
	private TernaryTreeNode<T> right;

	public TernaryTreeNode(T element) {
		this.element = element;
		left = null;
		center = null;
		right = null;
	}

	// Other implementation details omitted

}
```

Using this approach, we would need to define one Java class for _each_ type of N-ary tree!

- It is better to store the children of each node of an N-ary tree in an _array_:

```java
public class NaryTreeNode<T> {
	private T element;
	private NaryTreeNode<T>[] children;
	private int numChildren;

	public NaryTreeNode(int order, T element) {
		this.element = element;
		children = (NaryTreeNode<T>[]) new Object[order];
		numChildren = 0;
	}

	public void addChild(NaryTreeNode<T> child) {
		if(numChildren < children.length) {
			children[numChildren] = child;
			numChildren++;
		}
		else {
			// throw an exception (details omitted)
		}
	}

	// Other implementation details omitted

}
```