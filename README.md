# Workbook_PartB


### Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O)


#### **QUICK SORT**


The Quick Sort algorithm works by partitioning the array to be sorted, then recursively sorting each of the segments respectively. For this algorithm, one of the elements is selected at random to provide as the pivot point. The values smaller than the pivot value are then placed to the left of the pivot, while the remaining values are positioned to the right. This process then recursively repeats the algorithm for both halves of the original array.


~Explanation using an example of python code~


The pivot chosen always divides the array into two nearly equal halves. This means the size of the sub-arrays is consistently reduced by about half each time. The partitioning step has a time complexity of O(𝑛), given we need to go through all the elements of the partition. Furthermore, the depth of recursion is log 𝑛, as the array is divided into two halves each time. This means that in the base case scenario, the total time complexity will be O(𝑛 log 𝑛). However, with Big O Notation it is customary to calculate the time complexity of the worst case scenario. This algorithm is largely impacted by which element is chosen as the pivot point: the worst-case efficiency ( O(𝑛 2)) occurs when the pivot selection consistently results in highly unbalanced partitions (Pandey 2008). A common example that culminates in this result is when the left-most (or right-most) element is chosen as the pivot in a sorted or nearly sorted array. In this scenario, each partitioning step takes O(𝑛) time, in that we need to scan the entire array to divide it into two sub-arrays. Similarly, given each partition results in one empty sub-array and another sub-array with 𝑛 - 1 elements, the depth of recursion is 𝑛. Thus, the total time complexity in this scenario is O(𝑛) x O(𝑛) = O( 𝑛 2). These outcomes can be mitigated using strategies like choosing a random pivot or using the median-of-three method (choosing the median of the first, middle, and last elements) to improve the chances of more balanced partitions and thus better average-case performance (Pandey 2008).


Quick Sort is fast and efficient in practice due to good cache performance and fewer data movements compared to other O(𝑛 log 𝑛) algorithms. In this way, this algorithm is appropriate if sorting speed is paramount. As it is an in-place algorithm, this algorithm only requires a relatively small amount of storage space; making it advantageous when run on machines with limited storage space. Optimally, this algorithm is recommended in the case of repetitive data sets, sorting medium-to-large sized arrays and as a default choice when one is unsure which algorithm to employ (Pandey 2008). However, given that the relative order of elements may not be preserved, this algorithm is not considered stable. In addition to that, the fact that this sorting method is highly sensitive to pivot selection is a limitation, as it may lead to worst-case performance.



#### **MERGE SORT**


The Merge Sort algorithm takes a "divide and conquer" approach when sorting an array. It works by dividing the input data into two equal halves, and placing them into separate arrays. This process continues until we have 𝑛 sublists, each containing one element. Each array is then recursively sorted, and then merged back together to form the final sorted output. The number of levels of recursion needed to reach single-element sublists is logarithmic with respect to the size of the input array. In the worst-case scenario, merging two sorted sublists of size 𝑛/2 each takes O(𝑛) time. Therefore, when accounting for the divide step, there are  O(log 𝑛) levels of recursion. As is the case for most recursive sorts, this will result in a total time complexity of O(𝑛 log 𝑛) for this algorithm (Pandey, 2008).


~Explanation using example of python code~


In each merge step, all the elements of the array are visited once. This step involves comparing and merging elements of the two sorted halves. The time complexity of the merge step is linear with respect to the size of the array being merged. Since we have O(log 𝑛) levels of recursion (as determined by the divide step) and each level's merge step takes O(𝑛) time, the total time complexity for merging is O(𝑛 log 𝑛). This consistency in time complexity, irrespective of the input data, makes this algorithm particularly reliable for larger data sets. Furthermore, its preservation of the relative order of equal elements makes this a 'stable' option.


Merge Sort, while marginally faster than Heap Sort for larger datasets, demands twice the memory due to its use of a secondary array (Pandey, 2008.). This heightened memory necessity renders it less appealing for most applications, particularly when run on machines with limited memory (Pandey, 2008.). It's space complexity O(𝑛) is predictable and consistent, as it doesn't depend on the input size. However, this higher space complexity can also be considered a drawback when dealing with larger datasets, as it requires additional memory. Therefore, while merge sort has a good theoretical time complexity, it may potentially be a less attractive option in practice.



#### **COMPARISON**


Although the Quick Sort algorithm is exponentially faster than merge sort in practice, it's limited by its instability. Despite its smaller constant factors and better cache locality, the performance efficiency has the capacity to suffer depending on poor pivot selection, especially for certain types of data. Furthermore, although Quick Sort has an average-case time complexity of O(𝑛 log 𝑛), its worst-case time complexity is O(𝑛^2) (as a result of its sensitivity to pivot selection). This makes it both less stable and less predictable than Merge Sort in worst-case scenarios. Having said that, Quick Sort has a lower space complexity of O(log 𝑛) compared to Merge Sort's O(𝑛), making it more memory-efficient for large datasets.


In summary, as is the case with all algorithms, the choice between these two sorting methods depends on the specific requirements of the problem and the characteristics of the input data. While Quick Sort is often chosen for its average-case efficiency, lower space complexity and memory-efficiency; Merge Sort is preferred for its stability, consistent performance and ability to handle larger data sets.





### Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O)


#### **BINARY SEARCH**


The binary search algorithm, also known as half-interval search, logarithmic search, or binarychop, is a search algorithm that is used to find a particular element within a sorted array (Lin 2019). It works by repeatedly dividing the search interval in half and comparing the target value to an element in the middle of the array; if the value is less than the middle element, the right subarray of the array will be eliminated and the search will be narrowed to the left subarray. This process repeats until the target value is found.


Binary search operates by halving the search space in each step, resulting in a logarithmic time complexity. This means that in the worst case scenario, binary search runs in logarithmic time; making 𝑂(log 𝑛) comparisons, where 𝑛 is the number of elements in the array (Lin 2019). Given the nature of the algorithm, the time required will grow logarithmically with the size of the input. Therefore, if you double the size of the input, the time increases only by a constant amount. For example, if an array has 100 elements, a worst-case scenario denotes that a binary search might require up to approximately 7 comparisons before finding the target value (since log₂(100) ≈ 7).


```
Consider this sorted array: [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]


Say we want to find the target value 11.


Step 1:


low = 0, high = 9
mid = (0 + 9) / 2 = 4
The element at index 4 is 9.
Since 11 > 9, update low to mid + 1 = 5.
Step 2:


low = 5, high = 9
mid = (5 + 9) / 2 = 7
The element at index 7 is 15.
Since 11 < 15, update high to mid - 1 = 6.
Step 3:


low = 5, high = 6
mid = (5 + 6) / 2 = 5
The element at index 5 is 11.
Since 11 == 11, the search is successful.
```


In each step of the binary search, the size of the search interval is halved. Thus, if we start with 𝑛 elements, the number of elements to consider reduces as follows:
```
𝑛 → 𝑛/2 → 𝑛/4 → ... → 1
```
The number of steps required is the number of times we can divide n by 2 until we get 1, which is equivalent to the logarithm base 2 of 𝑛 (log₂ 𝑛). Therefore, the time complexity of binary search is O(log 𝑛).


While the logarithmic run time is advantageous in larger data sets, Binary Search is limited by the requirement for the array to be already sorted: potentially requiring an additional step.





#### **LINEAR SEARCH**


Linear Search is a simple and straight-forward algorithm that iterates through an array sequentially until the target value is found or the end of the array is reached. It starts at the beginning, comparing each element with the target value and moving linearly. If the end of the array is reached without finding the target, a signal (commonly -1) is returned to indicate the target element was not found.


```
Example
Consider an array: [4, 2, 7, 1, 9, 3], and we want to find the target value 9.


Step 1:


Compare the target value 9 with the first element 4.
9 does not equal 4, so move to the next element.
Step 2:


Compare 9 with the second element 2.
9 does not equal 2, so move to the next element.
Step 3:


Compare 9 with the third element 7.
9 does not equal 7, so move to the next element.
Step 4:


Compare 9 with the fourth element 1.
9 does not equal 1, so move to the next element.
Step 5:


Compare 9 with the fifth element 9.
9 equals 9, so the search is successful, and the index 4 is returned.
```


The time complexity of the linear search algorithm is determined by how many elements need to be checked to find the target value or to determine that it is not in the array. Given that the time required grows linearly with the size of the input: giving it a worst-case time complexity of 𝑂(𝑛). Meaning that if the size of the input doubles, the time taken will also double. In this way, this algorithm is most appropriately applicable to short arrays or small data sets. Having said that, as opposed to Binary Search, this algorithm can be applied to both sorted and unsorted arrays. For example, if an array has 100 elements, a linear search might need up to 100 comparisons in the worst case.




#### **COMPARISON**


When analysing the time complexity using Big O Notation, the logarithmic time complexity of Binary Search deems it the more efficient option; as it grows much more slowly than linear time complexity. Algorithms with 𝑂(log 𝑛) complexity scale better with increasing input sizes and can subsequently handle larger data sets more efficiently. In comparison, Linear Search has a worst-case performance of 𝑂(𝑛). Given the sequential nature of this algorithm, it ultimately has an 𝑂(𝑛) complexity in that the time required grows linearly with the size of the input: Thus making it an inefficient choice for larger datasets. Having said that, Binary Search's main limitation is that it requires the array to be already sorted.


In conclusion, while Linear Search is straightforward and works on unsorted arrays, Binary Search provides much better performance on sorted arrays with its logarithmic time complexity. The choice between them depends on the nature of the data (sorted or unsorted) and the size of the dataset, with binary search being the preferred choice for large sorted datasets where efficiency is critical.





#### **REFERENCES**


Abdel-Hafeez, S. and Gordon-Ross, A., 2017. An Efficient O ($ N $) Comparison-Free Sorting Algorithm. IEEE Transactions on Very Large Scale Integration (VLSI) Systems, 25(6), pp.1930-1942.


Pandey, R.C., 2008. Study and Comparison of various sorting algorithms. Computer Science and Engineering.


Lin, A., 2019. Binary search algorithm. WikiJournal of Science, 2(1), pp.1-13.


