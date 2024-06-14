# Workbook_PartB

### Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O)






BIG O NOTATION
- The notation is used to express the running times of algorithms in terms of input sizes. When an algorithm is documented to take time O(f(x)) on input x, the definition of Big O requires that the domain of the function is the set of natural numbers. 


**QUICK SORT**

(Pandey 2008)
- in-place, divide-and-conquer, massively recursive sort
- essentially a faster in-place version of the merge sort
- simple in theory but v difficult to translate to code
- this algorithm is largely impacted by which element is chosen as the pivot point - the worse-case efficieny ( O(_n_ 2)) occurs when the list is sorted and the left-most element is chosen
- Randomly choosing a pivot point (rather than using the left most element) is recommended if the data to be sorted isn't random
- If the pivot point is chosen at random, then the algorithmic complexity remains O(_n_ log _n_)
- By far the fastest
- Much like merge sort, this algorithm has 2 phases: a partition phase and a sort phase.
- Partition phase: all items <= pivot item are placed in one partition, while all items greater than a pivot are placed in another partition.
- Maintain a left and right search pointer.
- Quick sort has an average order of operation of O(n × log(n)), but when the partitions are
not anywhere near even, the order of operation approaches O(n2). For sorted lists and reverse sorted lists quick sort is an O(n2) algorithm. 

The recursive algorithm consists of four steps (which closely resemble the merge sort):
i) If there is one or less element in the array to be sorted, return immediately.
ii) Pick an element in the array to serve as a "pivot" point. (Usually the left-most
element in the array is used.)
iii) Split the array into two parts - one with elements larger than the pivot and the
other with elements smaller than the pivot.
iv) Recursively repeats the algorithm for both halves of the original array. 


- Quick sort is efficient only on the average, and its worst case is n2, while heap sort has an interesting property that the worst case, is not much different form the average case.
- The data set which we want to sort can come in three form completely sorted, inversely sorted and almost sorted. Some algorithms does not take any advantage of sorted order of data sequence like quick sort. 





**MERGE SORT**


The merge sort algorithm takes a "divide and conquer" approach when sorting an array. It works by dividing the input data into two equal halves, and placing them into separate arrays. This process contiues until we have _n_ sublists, each containing one element. Each array is then recursively sorted, and then merged back together to form the final sorted output. The number of levels of recursion needed to reach single-element sublists is logarithmic with respect to the size of the input array. In the worst-case scenario, merging two sorted sublists of size _n_/2 each takes O(_n_) time. Therefore, when accounting for the divide step, there are  O(log _n_) levels of recursion. As is the case for most recursive sorts, this will result in a total time complexity of O(_n_ log _n_) for this algorithm (Pandey, 2008).

~Explanation using example of python code~

In each merge step, all the elements of the array are visited once. This step involves comparing and merging elements of the two sorted halves. The time complexity of the merge step is linear with respect to the size of the array being merged. Since we have O(log _n_) levels of recursion (as determined by the divide step) and each level's merge step takes O(_n_) time, the total time complexity for merging is O(_n_ log _n_). This consistency in time complexity, irrespective of the input data, makes this algorithm particularly reliable for larger data sets. Furthermore, it's preservation of the relative order of equal elements makes this a 'stable' option.

Merge sort, while marginally faster than heap sort for larger datasets, demands twice the memory due to its use of a secondary array (Pandey, 2008.). This heightened memory necessity renders it less appealing for most applications, particularly when run on machines with limited memory (Pandey, 2008.). It's space complexity ( O(_n_) ) is predictable and consistent, as it doesn't depend on the input size. However, this higher space complexity can also be considered a drawback when dealing with larger datasets, as it requires additional memory. Therefore, while merge sort has a good theoretical time complexity, it may potentially be a less attractive option in practice. 




**COMPARISON**

Although the quick sort algorithm is expoentially faster than merge sort in practice, it's limited by it's instability. Despite it's smaller constant factors and better cache locality, the performance efficiency has the capacity to suffer depending on poor pivot selection, especially for certain types of data. Furthermore, although Quick Sort has an average-case time complexity of O(_n_ log _n_), its worst-case time complexity is O(_n_^2) (as a result of its sensitivity to pivot selection). This makes it both less stable and less predictable than Merge Sort in worst-case scenarios. Having said that, Quick Sort has a lower space complexity of O(log _n_) compared to Merge Sort's O(_n_), making it more memory-efficient for large datasets.

In summary, as is the case with all algorithms, the choice between these two sorting methods depends on the specific requirements of the problem and the characteristics of the input data. While Quick Sort is often chosen for its average-case efficiency, lower space complexity and memory-efficiency; Merge Sort is preferred for its stability, consistent performance and ability to handle larger data sets.





### Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O)



**RUBRIC**
- Demonstrates algorithic understanding (4 pts)
    > Provides a full and clear explanation for all algorithms, showcasing exceptional understanding in each explanation.

- Explains Big O notation calculations (4 pts)
    > Provides clear explanations for all four algorithms, describing how the Big O notation numbers were calculated. Demonstrates an excellent understanding of the relationship between algorithmic structures and Big O complexity.

- Utilises Big-O notation to analyse algorithm efficiency and applicability (4 pts)
    > Provides a comprehensive evaluation of algorithm efficiency using Big O notation. Explicitly compares the two algorithms in each pair and considers their practical applicability. Provides insightful discussions on edge cases. Demonstrates a high-level understanding of the implications of time complexity in practical use cases.


**REFERENCES**

Abdel-Hafeez, S. and Gordon-Ross, A., 2017. An Efficient O ($ N $) Comparison-Free Sorting Algorithm. IEEE Transactions on Very Large Scale Integration (VLSI) Systems, 25(6), pp.1930-1942.

Pandey, R.C., 2008. Study and Comparison of various sorting algorithms. Computer Science and Engineering.

