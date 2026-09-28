
Sorting algorithms take an input of unsorted data and output the data sorted given the sorting condition (ascending/descending) 

Sorting algorithms provide a essential way to simplify alot of complex problems and make code more efficient which are used in:
- searching 
- databases
- divide and conquer strategies
- data structures (trees)

## Types of sorting

There are many different types of sorting algorithms that differ depending on situation

| Sort Type        | Explanation                                                                                                                 |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------- |
| In-place sorting | Uses constant space to produce an output which means that it just directly modifies the array without creating copies of it |
| Internal sorting | All data is placed in **main memory**. In internal sorting, the problem cannot take input beyond allocated memory size      |
| External sorting | When all the data that needs to be sorted cannot be placed directly in memory. This is generally used with **massive data** |
| Stable sorting   | When two of the same item appear in the **same order** in the resulting data as it was in the **original unsorted data**    |
| Hybrid sorting   | Using more than **one type** of sorting algorithm to solve the problem                                                      |

## Sorting Algorithms

| $n$ame                                                                          | Best Case      | Average Case      | Worst Case        | Memory | Stable | Method Used         |
| ------------------------------------------------------------------------------- | -------------- | ----------------- | ----------------- | ------ | ------ | ------------------- |
| [Quick Sort](https://www.geeksforgeeks.org/dsa/quick-sort-algorithm/)           | $n \cdot logn$ | $n \cdot logn$    | $n^2$             | $logn$ | No     | Partitioning        |
| [Merge Sort](https://www.geeksforgeeks.org/dsa/merge-sort/)                     | $n \cdot logn$ | $n \cdot logn$    | $$n \cdot logn$$  | n      | Yes    | Merging             |
| [Heap Sort](https://www.geeksforgeeks.org/dsa/heap-sort/)                       | $n \cdot logn$ | $n \cdot logn$    | $n \cdot logn$    | 1      | No     | Selection           |
| [Insertion Sort](https://www.geeksforgeeks.org/dsa/insertion-sort-algorithm/)   | n              | $n^2$             | $n^2$             | 1      | Yes    | Insertion           |
| [Tim Sort](https://www.geeksforgeeks.org/dsa/timsort/)                          | n              | $n \cdot logn$    | $n \cdot logn$    | n      | Yes    | Insertion & Merging |
| [Selection Sort](https://www.geeksforgeeks.org/dsa/selection-sort-algorithm-2/) | $n^2$          | $n^2$             | $n^2$             | 1      | No     | Selection           |
| [Shell Sort](https://www.geeksforgeeks.org/dsa/shell-sort/)                     | $n \cdot logn$ | $n^{\frac{4}{3}}$ | $n^{\frac{3}{2}}$ | 1      | No     | Insertion           |
| [Bubble Sort](https://www.geeksforgeeks.org/dsa/bubble-sort-algorithm/)         | n              | $n^2$             | $n^2$             | 1      | Yes    | Exchanging          |
| [Cycle Sort](https://www.geeksforgeeks.org/dsa/cycle-sort/)                     | $n^2$          | $n^2$             | $n^2$             | 1      | No     | Selection           |
