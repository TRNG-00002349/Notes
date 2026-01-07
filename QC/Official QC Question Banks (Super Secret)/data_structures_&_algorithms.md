## Unit

# Data Structures & Algorithms

## Links

* [Required Questions](#required-questions)

## Required Questions

[Back to top](#unit)

* **Explain time-space complexity using Big O notation. How would you analyze the efficiency of a sorting algorithm?**
  * Keywords, concepts, or topics that should be in the response:
    * Time complexity measures operations relative to input size
    * Space complexity measures memory usage
    * Common complexities: O(1), O(log n), O(n), O(n log n), O(n²)
    * Worst-case vs. average-case analysis
  * Possible follow-up questions
    * What's the difference between O(n) and O(n²) with a practical example?
    * Why is O(log n) considered efficient?
    * How would you compare the time complexity of merge sort vs. bubble sort?

* **Describe trade-offs between arrays and linked lists. When would you choose one over the other?**
  * Keywords, concepts, or topics that should be in the response:
    * Array: contiguous memory, random access, fixed size
    * Linked list: dynamic size, sequential access, pointer overhead
    * Insertion/deletion efficiency differences
    * Memory allocation characteristics
  * Possible follow-up questions
    * In what scenario would a linked list outperform an array?
    * How do cache mechanisms affect array vs. linked list performance?
    * What's the time complexity for accessing the middle element in each?

* **Explain recursion and its trade-offs. When is it preferable to iteration?**
  * Keywords, concepts, or topics that should be in the response:
    * Base case and recursive case
    * Call stack usage and stack overflow risk
    * Memory overhead vs. code simplicity
    * Tail recursion optimization
  * Possible follow-up questions
    * How would you convert a recursive Fibonacci to iterative?
    * When does recursion make problems like tree traversal easier?
    * What's the space complexity of a recursive depth-first search?

* **How would you efficiently find duplicates in an array?**
  * Keywords, concepts, or topics that should be in the response:
    * Brute-force O(n²) solution
    * Sorting-based O(n log n) solution
    * Hash table O(n) solution
    * Trade-offs between time/space complexity
  * Possible follow-up questions
    * How would your solution change if memory is constrained?
    * What if the array contains 10 million elements?
    * How would you handle this for distributed systems?
