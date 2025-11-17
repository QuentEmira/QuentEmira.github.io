Containers is a term for any structure that is capable of storing a certain amount of specific kinds of data. The are also sometimes called collections. Below will be a list of common containers that are used:
1. Array: This is a contiguous block of memory that is used as a container. The size is predetermined (it is static), and is assigned during compile time.
2. Dynamic Array: Array's that can change size. This is usually allocated during runtime. An example is vector is C++.
3. Linked List: A structure made up of nodes. Each node connects to another node, forming a 'linked list'. The memory here does not have to be contiguous.
4. Stack: A specific implementation that follows LIFO (Last In First Out) ordering of elements.
5. Queue: A specific implementation that follows FIFO (First In First Out) ordering of elements.
6. Dequeue: A Double Ended Queue. In this struct, elements can be freely added and removed from both sides. A very useful struct.
7. Tree: A hierarchical way of grouping nodes, where each node has 0 or more parent nodes, and 0 or more child nodes. A variant of DAG.
8. Binary Search Tree: A specific type of tree where each node has at most two children, and the order of the children nodes is decided based on an order property.
9. Binary Heap: A self balancing tree, that balances itself based on two properties. The first is the 'shape property', which basically suggests that the tree be fully filled, and that the last row of the tree is filled from left to right. The second is the 'heap property', which suggests that there is a property by which a node is 'greater than' or 'equivalent to' its children node.
10. Priority Queue: A priority queue is like a self sorting list, where elements can be entered in any order, but can only leave based on a specific order, which would be its priority. It is generally not implemented using a list, but rather a heap.
11. Dictionary: A struct with keys, and associated values. The keys are mapped to the values, and thus the values can be easily obtained using the keys.
12. Set: A struct that ensures that all elements with it are always unique, not recording any duplicate values.
13. Graph: A collection of nodes connected to one another by unidirectional or bidirectional pathways in an arbitrary pattern.
14. Directed Acyclic Graph: A collection of nodes with only unidirectional pathways, that has no cycles.

### Common Functions
While we do have different implementations for containers, these containers have some common functionalities:
- Add: This function is used to add an element into the container.
- Delete: This function is to remove an element from the container.
- Find: Search an element in the container to find its location.
- Sort: This function goes through the struct and sorts it, if possible.
- Sequential Access: Used to access the next element in the sequence, if a sequence exists.
- Random Access: Used to randomly access an element if possible.