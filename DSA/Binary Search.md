
A binary search is a searching algorithm where it takes the midpoint of two indices (pointers) and compares the midpoint of the array with the key its looking for and does that until its found the key within the array or exhaust the array.

![[frame_1.webp]]

There a 2 conditions that **MUST** be true before apply a binary search to a dataset:

- The dataset must be sorted **OR** in a monotonic search space (follows a consistent pattern)
- Access to the element must be constant time ($O(n)$)

Binary searches follow the following steps:

1. Divide the search space into two halves by ****finding the middle index "mid"****. 
2. Compare the middle of the search space with the **key**. 
3. If the ****key**** is found at middle, the process is terminated.
4. If the ****key**** is not found at middle, choose which half will be used as the next search space.  
    -> If the ****key**** is smaller than the middle, then the ****left**** side is used for next search.  
    -> If the ****key**** is larger than the middle, then the ****right**** side is used for next search.
5. This process is continued until the ****key**** is found or the total search space is exhausted.1

**NOTE:** the mathematical equation for solving the **midpoint** can differ between data structures, but generally


| Data structure  | Equation                       | Why?                                                                                                                |
| --------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| Arrays          | $mid = low + (high - low) / 2$ | This equation ensures that all elements are included within the search including **the first** and **last element** |
| Monotonic space | $mid = (low + high) / 2$       | The general case for when we're dealing with numbers                                                                |
