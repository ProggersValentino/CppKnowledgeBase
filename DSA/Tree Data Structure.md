
A tree data structure is a hierarchical data structure that is used to organize data in a parent child relationship.

It consists of nodes where the topmost node is the **root node** and every other node can have one or more child nodes depending on the tree type![[3.webp]]

A tree also has height where for each node that is traversed down the tree increases the "depth"![[2.webp]]

#### Basic Terminology

| Term          | Meaning                                                | Example                                          |
| ------------- | ------------------------------------------------------ | ------------------------------------------------ |
| Parent Node   | A node that is an immediate predecessor of other nodes | node 32 is a parent node of nodes 3, 6           |
| Child node    | A node that is a successor of a parent node            | Nodes 7, 8 are child nodes of the parent node 40 |
| Leaf Node     | Nodes that do not have any child                       | Node 12 has no child nodes                       |
| Sibling       | Nodes that share the same parent                       | Node 12, 13, 15 parent's node is 6               |
| Internal Node | A node with atleast one child                          |                                                  |
| Subtree       | A node and its descendents form a subtree              |                                                  |
Nodes can be represented as classes or structs which define the data that each node will hold and an array variable holding other nodes which will be its children:
```cpp
class Node 
{
public:
	int data; 
	vector<Node*> children
	
	Node(int x)
	{
		data = x
	}
}
```


## Tree Types
There are many different types of trees

## Binary tree

binary tree only holds a maximum of two children 

**Full binary tree**: every node has a either 0 or 2 children
**Complete Binary tree**: all levels are fully filled except possibly the last 
**Balanced Binary Tree:** the height different between left and right subtrees of every node is minimal

## Ternary Tree
Each node can have at most three children, often labeled as left, middle, and right

## N-ary Tree (Generic)
