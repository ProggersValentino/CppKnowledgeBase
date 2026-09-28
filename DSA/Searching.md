
searching algorithms find a particular component or piece of data within a dataset like an array, tree, or other data representations.

aside from linear search, searching algorithms generally require the dataset to be in a sorted state before using attempting to search for the given. 
This allows for the algorithms to have a consistent average case when searching for a item.

## Searching Algorithms

| Algorithm                                                                       | Best Case | Average Case               | Worst Case         | Space  | Requirement         |
| ------------------------------------------------------------------------------- | --------- | -------------------------- | ------------------ | ------ | ------------------- |
| [Linear Search](https://www.geeksforgeeks.org/dsa/linear-search/)               | $O(1)$    | $O(n)$                     | $O(n)$             | $O(1)$ | Works on any data   |
| [Binary Search](https://www.geeksforgeeks.org/dsa/binary-search/)               | $O(1)$    | $O(log \cdot n)$           | $O(log \cdot n)$   | $O(1)$ | Sorted array needed |
| [Ternary Search](https://www.geeksforgeeks.org/dsa/ternary-search/)             | $O(1)$    | $O(log_3 \cdot n)$         | $O(log_3 \cdot n)$ | $O(1)$ | Unimodal data       |
| [Jump Search](https://www.geeksforgeeks.org/dsa/jump-search/)                   | $O(1)$    | $O(\sqrt{n})$                      | $O(\sqrt{n})$              | $O(1)$ | Sorted data         |
| [Interpolation Search](https://www.geeksforgeeks.org/dsa/interpolation-search/) | $O(1)$    | $O(log \cdot log \cdot n)$ | $O(n)$             | $O(1)$ | Uniform data        |
| [Fibonacci Search](https://www.geeksforgeeks.org/dsa/fibonacci-search/)         | $O(1)$    | $O(log \cdot n)$           | $O(log \cdot n)$   | $O(1)$ | Sorted data         |
| [Exponential Search](https://www.geeksforgeeks.org/dsa/exponential-search/)     | $O(1)$    | $O(log \cdot n)$           | $O(log \cdot n)$   | $O(1)$ | Sorted data         |
