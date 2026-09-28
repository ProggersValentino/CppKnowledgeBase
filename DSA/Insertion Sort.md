
Insertion sort works by shifting each element in an unsorted list into its sorted position and follows this pattern:

1. start with second element as the first element is assumed to be sorted
2. Compare second element with first, if second is smaller than first then swap values around
3. Move to the third element, compare the first two and put it in it's correct position, shift it to its position 
4. repeat until array is sorted 

## Complexity Analysis


| Complex Type     |                 | Analysis |
| ---------------- | --------------- | -------- |
| Time Complexity  |                 |          |
|                  | Best Case       | $O(n)$   |
|                  | Worst Case      | $O(n^2)$ |
|                  | Average Case    | $O(n^2)$ |
| Space Complexity |                 |          |
|                  | Auxiliary Space | $O(1)$   |


## Advantages

- Simple and easy to implement.
- ****Stable**** sorting algorithm.
- Efficient for small lists and nearly sorted lists.
- Space-efficient as it is an in-place algorithm.
- Adoptive. the [number of inversions](https://www.geeksforgeeks.org/dsa/inversion-count-in-array-using-merge-sort/) is directly proportional to number of swaps. For example, no swapping happens for a sorted array and it takes O(n) time only.

## Disadvantages

- Inefficient for large lists.
- Not as efficient as other sorting algorithms (e.g., merge sort, quick sort) for most cases.