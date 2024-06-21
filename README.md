# Workbook_PartB

### Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O)


#### **QUICK SORT**

The Quick Sort algorithm works by partitioning the array to be sorted, then recursively sort each of the segments respectively. For this algorithm, one of the elements is selected at random to provide as the pivot point. The values smaller than the pivot value are then placed to the left of the pivot, while the remaining values are positioned to the right. This process then recursively repeats the algorithm for both halves of the original array.

~Explanation using an example of python code~

The pivot chosen always divides the array into two nearly equal halves. This means the size of the sub-arrays is consistently reduced by about half each time. The partitioning step has a time complexity of O(𝑛), given we need to go through all the elements of the parition. Furthermore, the depth of recursion is log 𝑛, as the array is divided in into two halves each time. This means that in the base case scenario, the total time complexity will be O(𝑛 log 𝑛). However, with Big O Notation it is customary to calculate the time complexity of the worst case scenario. This algorithm is largely impacted by which element is chosen as the pivot point: the worse-case efficieny ( O(𝑛 2)) occurs when the pivot selection consistently results in highly unbalanced partitions (Pandey 2008). A common example that culnimates in this result is when the left-most (or right-most) element is chosen as the pivot in a sorted or nearly sorted array. In this scenario, each partitioning step takes O(𝑛) time, in that we need to scan the entire array to divide it into two sub-arrays. Similarly, given each partition results in one empty sub-array and another sub-array with 𝑛 - 1 elements, the depth of recursion is 𝑛. Thus, the total time complexity in this scenario is O(𝑛) x O(𝑛) = O( 𝑛 2). These outcomes can be mitigated using strategies like choosing a random pivot or using the median-of-three method (choosing the median of the first, middle, and last elements) to improve the chances of more balanced partitions and thus better average-case performance (Pandey 2008).

Quick Sort is fast and efficient in practice due to good cache performance and fewer data movements compared to other O(𝑛 log 𝑛) algorithms. In this way, this algorithm is appropriate if sorting speed is paramount. As it is an in-place algorithm, this algorithm only requires a relatively small amount of storage space; making it advantageous when run on machines with limited storage space. Optimally, this algorithm is recommended in the case of repetitive data sets, sorting medium-to-large sized arrays and as a default choice when one is unsure which algorithm to emply (Pandey 2008). However, given that the relative order of elements may not be preserved, this algorithm is not considered stable. In addition to that, the fact that this sorting method is highly sensitive to pivot selection is a limitation, as it may lead to worst-case peformance.



#### **MERGE SORT**


The Merge Sore algorithm takes a "divide and conquer" approach when sorting an array. It works by dividing the input data into two equal halves, and placing them into separate arrays. This process contiues until we have 𝑛 sublists, each containing one element. Each array is then recursively sorted, and then merged back together to form the final sorted output. The number of levels of recursion needed to reach single-element sublists is logarithmic with respect to the size of the input array. In the worst-case scenario, merging two sorted sublists of size 𝑛/2 each takes O(𝑛) time. Therefore, when accounting for the divide step, there are  O(log 𝑛) levels of recursion. As is the case for most recursive sorts, this will result in a total time complexity of O(𝑛 log 𝑛) for this algorithm (Pandey, 2008).

~Explanation using example of python code~

In each merge step, all the elements of the array are visited once. This step involves comparing and merging elements of the two sorted halves. The time complexity of the merge step is linear with respect to the size of the array being merged. Since we have O(log 𝑛) levels of recursion (as determined by the divide step) and each level's merge step takes O(𝑛) time, the total time complexity for merging is O(𝑛 log 𝑛). This consistency in time complexity, irrespective of the input data, makes this algorithm particularly reliable for larger data sets. Furthermore, it's preservation of the relative order of equal elements makes this a 'stable' option.

Merge Sort, while marginally faster than Heap Sort for larger datasets, demands twice the memory due to its use of a secondary array (Pandey, 2008.). This heightened memory necessity renders it less appealing for most applications, particularly when run on machines with limited memory (Pandey, 2008.). It's space complexity O(𝑛) is predictable and consistent, as it doesn't depend on the input size. However, this higher space complexity can also be considered a drawback when dealing with larger datasets, as it requires additional memory. Therefore, while merge sort has a good theoretical time complexity, it may potentially be a less attractive option in practice. 



#### **COMPARISON**

Although the Quick Sort algorithm is expoentially faster than merge sort in practice, it's limited by it's instability. Despite it's smaller constant factors and better cache locality, the performance efficiency has the capacity to suffer depending on poor pivot selection, especially for certain types of data. Furthermore, although Quick Sort has an average-case time complexity of O(𝑛 log 𝑛), its worst-case time complexity is O(𝑛^2) (as a result of its sensitivity to pivot selection). This makes it both less stable and less predictable than Merge Sort in worst-case scenarios. Having said that, Quick Sort has a lower space complexity of O(log 𝑛) compared to Merge Sort's O(𝑛), making it more memory-efficient for large datasets.

In summary, as is the case with all algorithms, the choice between these two sorting methods depends on the specific requirements of the problem and the characteristics of the input data. While Quick Sort is often chosen for its average-case efficiency, lower space complexity and memory-efficiency; Merge Sort is preferred for its stability, consistent performance and ability to handle larger data sets.




### Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O)



#### **BINARY SEARCH**


The binary search algorithm, also known as half-interval search, logarithmic search, or binarychop, is a search algorithm that is used to find a particular element within a sorted array (Lin 2019). It works by repeatedly dividing the search interval in half. It compares the target value to the middle of the array; if the value is less than the middle element, the right subarray of the array will be eliminated and the search will be narrowed to the left subarray. This process repeats until the target value is found.

Binary search operates by halving the search space in each step, resulting in a logarithmic time complexity. This means that in the worst case scenario, binary search runs in logarithmic time; making 𝑂(log 𝑛) comparisons, where 𝑛 is the number of elements in the array (Lin 2019). 

```
The time required grows logarithmically with the size of the input.
If you double the size of the input, the time taken increases only by a constant amount (logarithmically).
Example: If an array has 100 elements, a binary search might need up to about 7 comparisons in the worst case (since log₂(100) ≈ 7).
```
```
In each step of the binary search, the size of the search interval is halved. Thus, if we start with 𝑛 elements, the number of elements to consider reduces as follows:

n → n/2 → n/4 → ... → 1

The number of steps required is the number of times we can divide 𝑛 by 2 until we get 1, which is equivalent to the logarithm base 2 of 𝑛 (log₂ 𝑛). Therefore, the time complexity of binary search is 𝑂(log 𝑛).
```

While makes it much faster than linear search for large datasets, this algorithm can only be applied to sorted arrays, thus requiring an additional sorting step for unsorted arrays. Despite this drawback, binary search can be applied to a broader set of problems, including identifying the closest smaller or larger element in an array relative to a given target, even if the target is not present in the array (Lin 2019).






#### **LINEAR SEARCH**

```
The time required grows linearly with the size of the input.
If you double the size of the input, the time taken also doubles.
Example: If an array has 100 elements, a linear search might need up to 100 comparisons in the worst case.
```
```
1. Linear Search

Working:
Linear search is a straight-forward searching algorithm where each element of the array (or list) is checked sequentially until the target element is found or all elements have been checked. It works on both sorted and unsorted arrays.

Steps:

Start from the beginning of the array.
Compare each element with the target value.
If the element matches the target, return its index.
If the end of the array is reached without finding the target, return a signal (commonly -1) indicating the target is not in the array.
Efficiency (Big O):

Time Complexity: 𝑂(𝑛), where n is the number of elements in the array. This means in the worst-case scenario, linear search will have to scan the entire array once to find the target or determine it's not present.
Space Complexity: O(1). Linear search only requires a constant amount of additional space for variables regardless of the input size.
```


#### **COMPARISON**

When analysing the time complexity using Big O Notation, the logarithmic time complexity of Binary Search deems it the more efficient option; as it grows much more slowly than linear time complexity. Algorithms with 𝑂(log 𝑛) complexity scale better with increasing input sizes and can sunsequently handle larger data sets more efficiently. In comparison, Linear Search has a worst-case performance of 𝑂(𝑛). Given the sequential nature of this algorithm, it ultimately has an 𝑂(𝑛) complexity in that the time required grows linearly with the size of the input: Thus making it an inefficient choice for larger datasets. Having said that, Binary Search's main limtation is that it requires the array to be already sorted.

In conclusion, while Linear Search is straightforward and works on unsorted arrays, Binary Search provides much better performance on sorted arrays with its logarithmic time complexity. The choice between them depends on the nature of the data (sorted or unsorted) and the size of the dataset, with binary search being the preferred choice for large sorted datasets where efficiency is critical.


#### **RUBRIC**
- Demonstrates algorithic understanding (4 pts)
    > Provides a full and clear explanation for all algorithms, showcasing exceptional understanding in each explanation.

- Explains Big O notation calculations (4 pts)
    > Provides clear explanations for all four algorithms, describing how the Big O notation numbers were calculated. Demonstrates an excellent understanding of the relationship between algorithmic structures and Big O complexity.

- Utilises Big-O notation to analyse algorithm efficiency and applicability (4 pts)
    > Provides a comprehensive evaluation of algorithm efficiency using Big O notation. Explicitly compares the two algorithms in each pair and considers their practical applicability. Provides insightful discussions on edge cases. Demonstrates a high-level understanding of the implications of time complexity in practical use cases.


#### **REFERENCES**



Abdel-Hafeez, S. and Gordon-Ross, A., 2017. An Efficient O ($ N $) Comparison-Free Sorting Algorithm. IEEE Transactions on Very Large Scale Integration (VLSI) Systems, 25(6), pp.1930-1942.


Pandey, R.C., 2008. Study and Comparison of various sorting algorithms. Computer Science and Engineering.


Lin, A., 2019. Binary search algorithm. WikiJournal of Science, 2(1), pp.1-13.

