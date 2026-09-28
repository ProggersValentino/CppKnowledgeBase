[ref](https://www.geeksforgeeks.org/dsa/introduction-to-linked-list-data-structure/)

A linked list is a chain of nodes where each node references the next node to it. The references to the next nodes are generally memory pointers pointing to that node. 
![[Linked-list.webp]]
This allows for efficient insertion and deletion as:

- arrays are static in size meaning if you want to resize the array you need to create a whole new array with the new size and copy over from the original.
- vectors are dynamic, but when a vector expands its size, in the background, it wipes itself and then allocates a new block of memory to accompany the new size 

So linked lists provide the benefit of vectors being dynamic but don't need to reallocate when increasing its size. 

However, this does mean that the linked list is scattered across memory so you can't access a specific element immediately without needing to go through the entire list to find it. This makes a linked list cache inefficient

### Basic Terminologies

| Term         | Meaning                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------- |
| Head         | The head of the linked list is the initial node at the start of list, basically a root node |
| Node         | linked consist a series of nodes that connect together through references to the next node  |
| Data         | The data stored within each node                                                            |
| Next pointer | memory pointer or reference to the next node within the linked list                         |

## Types

There are also 3 different types of linked lists that you can incorporate:

### Single

The default data structure for a linked list where it consists of:

- The **data** you want to store in each node
- **Pointer reference** to the next node within the linked list
- The **last node** within the list has a pointer reference **NULL** for the next node

This means that you can only traverse the linked list from start to finish and it does not wrap around back to the beginning.
![[link1.webp]]
### Doubled

The double linked list expands from the single linked list consisting of:

- The **data** you want to store in each node
- **Pointer reference** to the next node within the linked list
- **Pointer reference** to the previous node
- The **last node** within the list has a pointer reference **NULL** for the next node
- the **first node** within the list has a **NULL** pointer reference for the previous node

This expands the traversal capabilities where now you are able to traverse through the linked list forwards and backwards
![[11 1.webp]]![[22.webp]]
### Circular

The circular linked list expands upon the doubled where it consists of:

- The **data** you want to store in each node
- **Pointer reference** to the next node within the linked list
- **Pointer reference** to the previous node
- The **last node** within the list has a pointer reference to the **first node** within the list
- the **first node** within the list has a pointer reference to the **last node** within the list
![[25.webp]]

![[26.webp]]