# Unit: Java Data Structures and Algorithms


| Unit | Importance |
| ---  | ---------- |
| Data Structures | [Critical](#importance-critical) |
| Data Structures | [High](#importance-high) |
| Data Structures | [Regular](#importance-regular) |
| Algorithims | [Critical](#importance-critical-1) |
| Algorithims | [High](#importance-high-1) |
| Algorithims | [Regular](#importance-regular-1) |

## Data Structures

### IMPORTANCE: CRITICAL
[Back to top](#unit-java-data-structures-and-algorithims)

*  **What are Data Structures?**
    * Keywords, concepts, or topics that should be in the response:
        - Is used to organize, manage and store data
        - Enables efficient access and modification when applied correctly to a specific situation/problem 
    * Possible follow-up questions:
        * What are some types of data structures? (Linked List, Array, Stack, Queue, Tree, Graph...)

* **What is a Linked List?**
    * Keywords, concepts, or topics that should be in the response:
        + Linear data structure, in which elements are not stored at contiguous memory locations
        + Elements are linked using pointers 
        + Linked lists are dynamic meaning that they can increase or decrease in size
    * Possible follow-up questions:
        * Where would we use Linked Lists/Doubly Linked Lists?
            - Can be used to implement various data structures like hash-tables, stacks, binary trees etc.
            - Can be used to implement functionalities such as undo/redo
            - Used by a thread scheduler in many OS to maintain a list of all running processes
            - Can also be used in games e.g. representing a deck of cards
            - Can be used in any software that requires forward and backward navigation e.g. music players, in web-browsers to move between previously visited and current page etc.

* **What is a Map?**
    * Keywords, concepts, or topics that should be in the response:
        - Has a key value pair and allows for fast look up for the value if the key is known
    * Possible follow-up questions:
        * What are some real world uses for maps?
            - A map of the zip code and cities
            - A map of regions and the countries in each region
        * Can maps contain duplicate keys? (No)
        * Do maps allow for null keys and null values?
            - Specific implmentations allow it such as HashMap and LinkedHashMap
            - TreeMap does not support null keys and null values

* **What is a Heap?**
    * Keywords, concepts, or topics that should be in the response:
        - Is a special type of tree where the tree is a complete binary tree
        - Generally 2 types of heap:
            - Max-Heap:
                - The root node must be the greatest among all of the elements present within the tree and all of the sub-nodes must also be larger than their children 
            - Min-Heap:
                - The root node must be the smallest among all the elements in the tree and all of the sub-nodes must also be smaller than their children
    * Possible follow-up questions:

* **What is a Stack?**
    * Keywords, concepts, or topics that should be in the response:
        - Linear data type with a predefined capacity or boundary
        - Last In First Out (LIFO) or First In Last Out (FILO) ordering
    * Possible follow-up questions:
        * What are some benefits of using stacks?
            - Implement functions, parsers, expression evaluation, and some algorithms
            - Great for processing nested structures
        * What would be a simple real-world application of a stack?
            - Reversing a string letter by letter
            - Undo and redo function on a computer or text editor
        * What are some common methods we can use with stacks?
            - push(ele), pop(), isEmpty(), peek()

* **What is a Queue?**
    * Keywords, concepts, or topics that should be in the response:
        - Linear structure that follows a First In First Out (FIFO) order
        - Queues open from both ends: One end for inserting data (enqueue), and the other for removing data (dequeue)
    * Possible follow-up questions:
        * What are some common methods we can use with stacks?
            - enqueue(ele), dequeue(), peekFirst(), peekLast()
        * What is the difference between a stack vs queue?
            - Stack is only open from one end
            - Stack: LIFO; Queue: FIFO

* **What is a Set?**
    * Keywords, concepts, or topics that should be in the response:
        - Stores unordered elements 
        - Cannot contain duplicate elements
    * Possible follow-up questions:

* **What is a Tree?**
    * Keywords, concepts, or topics that should be in the response:
        - The data structure is shaped like a tree
        - Each data element is stored in a node, all nodes are connected to each other in a hierarchical fashion
    * Possible follow-up questions:
        * Where would trees be useful?
            - Creating a family tree

* **What are the Primative Data Types?**
    * Keywords, concepts, or topics that should be in the response:
        * 8 of them
        * byte, short, int, float, char, boolean, long, and double
    * Possible follow-up questions:

* **What is the difference between an Array and LinkedList?**
    * Keywords, concepts, or topics that should be in the response:
        * Arrays have better cache locality that can make them better in terms of performance
        * It is easy to insert and delete elements in Linked List
        * Random access is not allowed in a typical implementation of Linked Lists
        * The size of array has to be pre-decided, linked lists can change their size any time
    * Possible follow-up questions:
        * When would we want to use a Linked List over an ArrayList?
            + When we have a ton of insertions and deletions
            + Linkedlist insertion/deletion is O(1) while ArrayList insertion/deletion is O(n)

* **How do you instantiate an empty Array List that contains a generic value?**
    * Keywords, concepts, or topics that should be in the response:
        * `ArrayList<T> myList = new ArrayList<T>();`
    * Possible follow-up questions:
        * How would I make it contain Strings? (Change the generic T with String)
        * Can an ArrayList take in primitive data types? (No, would need to use a wrapper class to convert to object; Ex: int to Integer)
        * How would you instantiate an empty Array that contains Strings of the city names? ( `String[] city` ) 

* **What is the difference between a HashSet vs HashMap?**
    * Keywords, concepts, or topics that should be in the response:
        * Set: no duplicates, slower, use add() to input values
        * Map: duplicates, faster b/c of key:value pairs, use put()to input values
    * Possible follow-up questions:

* **What is the difference between a TreeMap vs HashMap?**
    * Keywords, concepts, or topics that should be in the response:
        * Tree: No null keys; only homogenous values (sorting on keys); faster (O(1)); get() and set()
        * Hash: Single null key; can have heterogeneous values (no sorting on keys); slower (O(log(n))); add(), remove(), contains()
    * Possible follow-up questions:

* **How would you create a HashMap that contains city capitals and their corresponding country? Type it in the chat?**
    * Keywords, concepts, or topics that should be in the response:
        * `HashMap<String, String> capitals = new HashMap<String, String>();`
    * Possible follow-up questions:
        * What does the first String value represent? (the Key)
        * What does the second String value represent? (the Value)
        * How would you add an entry to the HashMap? (`capitals.put("England", "London");` or the put() method)
        * How would you access a value? (get() and refer to the key or first value)
        * How would you delete an item? (remove() and refer to the key or first value)
        * How would you delete the entire content of the HashMap? (clear())



### IMPORTANCE: HIGH
[Back to top](#unit-java-data-structures-and-algorithims)

* **What is a Single Linked List?**
    * Keywords, concepts, or topics that should be in the response:
        + Defined as all nodes are linked together in a few sequential manner, hence it is also known as a linear linked list
        + Clearly is has the beginning and the end. 
        + Main problem is that we cannot access the predecessor of the node from the current node
    * Possible follow-up questions:
        * What are some advantages of a singly linked list?
            + Insertions and deletions can be done easily in O(1) time
            + Space is not wasted as we can get space according to our requirements
        * What are some disadvantages of a singly linked list?
            + Accessing the preceding node of a current node is not possible as there is no backward traversal
            + If we have to go to a particular element then we have to go through all those elements that come before that element in O(n) time
            + We cannot traverse it starting from the end node, we can only do so from the beginning first node

* **What is a Double Linked List?**
    * Keywords, concepts, or topics that should be in the response:
        + Similar to a linked list but here each node has an extra pointer that stores the address of the previous node 
        + Internally, the `java.util.LinkedList` is implemented using a Doubly Linked List Data Structure
    * Possible follow-up questions:
        * What are some advantages to a Doubly Linked List?
            + Allows us to iterate in both directions
            + We can delete a node easily as we have access to its previous node
            + Reversing is easy
        * What are some disadvantages to a Doubly Linked List?
            + Compared to a singly linked list, each node stores an extra pointer which consumes extra memory
            + Operations require more time due to the overhead of handling extra pointers as compared to singly-linked lists

* **What is a Hash Set?**
    * Keywords, concepts, or topics that should be in the response:
        - Hash set stores the elements by using a mechanism called hashing
        - HashSet contains unique elements only
        - HashSet allows null values
        - HashSet is non-synchronized
    * Possible follow-up questions:
        * Create a HashSet object called `names` that will store strings and type it in chat. ( `HashSet<String> names = new HashSet<String>();` )

* **Create a TreeMap object called `roster` that will have an Integer Key and a String Value.**
    * Keywords, concepts, or topics that should be in the response:
        * `TreeMap<Integer, String> roster = new TreeMap<Integer, String>();`
    * Possible follow-up questions:
        * How would you add a value to the TreeMap? (put())
        * How would you retrieve an item from the TreeMap? (get(Object Key))

* **What are the Non-Primative Data Structures?**
    * Keywords, concepts, or topics that should be in the response:
        * Linear: each element is connected to one other element only (Arrays, Stack, Queue, Linked List)
        * Non-Linear: each element is connected to n-other elements (Trees, Graph, Heap, Hash)
    * Possible follow-up questions:

* **What is a Static Data Structure? Give an example?**
    * Keywords, concepts, or topics that should be in the response:
        * size is declared and fixed at Compile Time and cannot be changed later
        * Array (only one)
    * Possible follow-up questions:

* **What is a Dynamic Data Structure? Give examples?**
    * Keywords, concepts, or topics that should be in the response:
        * size is not fixed at compile time and can be decided at runtime depending upon requirements
        * Linked List, Stack, Queue
    * Possible follow-up questions:



### IMPORTANCE: REGULAR
[Back to top](#unit-java-data-structures-and-algorithims)

* **What is a Deque?**
    * Keywords, concepts, or topics that should be in the response:
        - Elements can be added or removed from either the front or back of the queue
        - Short for double ended queue
    * Possible follow-up questions:

* **How is a Graph different than a Binary Tree?**
    * Keywords, concepts, or topics that should be in the response:
        - We need to track a node if it has been visited before or not in a graph
        - Can easily accomplish tracking a node with a boolean variable 
        - If node have been visited then we won't visit it again
    * Possible follow-up questions:

* **What is a Spanning Tree?**
    * Keywords, concepts, or topics that should be in the response:
        - Is a subgraph of an undirected connected graph
    * Possible follow-up questions:
        * What is a minimum spanning tree?
            - A spanning tree but the sum of the weights of the edge is minimum
            - The weights of the spanning tree is the sum of the weights given to the edges of the spanning tree

* **What is a Graph?**
    * Keywords, concepts, or topics that should be in the response:
        - A non-linear data structure consisting of nodes and edges
        - Nodes are sometimes also referred to as vertices
        - Edges are just lines or arcs that connect any 2 nodes in the graph
    * Possible follow-up questions:
        * What types of real world applications would we see graphs being implemented?
            - Commonly used in social networks like linkedIn, Facebook
            - Each person is represented with a node, each node is a structure and contains info such as a person's id, name, gender, locale, etc.



## Algorithims

### IMPORTANCE: CRITICAL
[Back to top](#unit-java-data-structures-and-algorithims)

* **What is an Algorithm?**
    * Keywords, concepts, or topics that should be in the response:
        - Is a set of instructions for solving a problem 
        - One example would be a recipe, it tells us how to create a dish, and what ingredients we would need
    * Possible follow-up questions:

* **What is Time Complexity?**
    * Keywords, concepts, or topics that should be in the response:
        + The amount of time taken by an algorithm to run, as a function of the length of the input. It measures the time taken to execute each statement of code in an algorithm
        + Measured by Big O Notation
    * Possible follow-up questions:
        * What is Big O notation?
            - Is a way developers can use to analyze the running time of algorithms
        * What is the slowest time complexity? (O(n<sup>n</sup>))
        * What is the quickest time complexity? (O(1))

* **Explain the concept of Binary Search?**
    * Keywords, concepts, or topics that should be in the response:
        + Search a sorted array by repeatedly dividing the search interval in half
        + If x is less than the item in the middle, look for the left half
        + If x is higher than mid, then we look at the right 
    * Possible follow-up questions:
        * What is the time complexity of Binary Search? (O(log n))

* **What is Merge Sort?**
    * Keywords, concepts, or topics that should be in the response:
        + Uses the `divide and conquer` strategy for sorting elements in an array 
        + Recursively breaking down a problem into 2 or more sub-problems of the same or related type
    * Possible follow-up questions:
        * What is the time complexity of Merge Sort?
            - Runtime is O(n log n) which is much faster and requires less operations than Insertion or Selection Sort O(n<sup>2</sup>)
    
* **What is Bubble Sort?**
    * Keywords, concepts, or topics that should be in the response:
        - Swaps adjacent elements repeatedly if they are in the wrong order
    * Possible follow-up questions:
        * What are some downsides to Bubble Sort?
            - The algorithm needs 1 whole extra pass to know if the array is sorted even after the array is done being sorted

* **Explain the concept of Brute Force?**
    * Keywords, concepts, or topics that should be in the response:
        - Systematically checking for all possible solutions through an exhaustive search 
    * Possible follow-up questions:
        * What are some benefits to Brute Force?
            - Allows us to reach the solution faster if we do not know about the correct data structure to solve the problem in the most efficient manner
            - Generally the first thing that comes to mind when solving coding challenges so it's simply the easiest go-to solution
        * What are some downsides to Brute Force?
            - May not be the most optimal solution to a certain problem in the majority of cases
            - May easily run out of time due to the exhaustive search nature, brute force would have to check against all values which is time consuming, with problems that have runtime constraints this would not be ideal



### IMPORTANCE: HIGH
[Back to top](#unit-java-data-structures-and-algorithims)

* **What is Space Complexity?**
    * Keywords, concepts, or topics that should be in the response:
        + Measures the total amount of memory an algorithm or operation needs to run according to its input size
    * Possible follow-up questions:
        * How is space complexity influenced by time complexity? 
            * Faster speed = More space
            * More optimized Time Complexity means less optimized Space Complexity

* **What is Recursion?**
    * Keywords, concepts, or topics that should be in the response:
        - Occurs when a method invokes itself
    * Possible follow-up questions:
        * What is a potential side effect of Recursion? (Stack Overflow Error: stack runs out of space/memory)
        
* **What is this code doing and what will eventually happen?**
    ```java
    public static void foo() {
        foo();
    }
    ```
    * Keywords, concepts, or topics that should be in the response:
        * Recursion
        * The above will keep calling itself and adding 1 frame on top of another in the stack until we reach a StackOverflowError so we must add a condition for the method to be invoked
    * Possible follow-up questions:

* **What is Heap Sort?**
    * Keywords, concepts, or topics that should be in the response:
        + Eliminate the elements one by one from the heap part of the list, and then insert them into the sorted part of the list
    * Possible follow-up questions:
        * How does heap sort work?
            - 2 phases
            - First step includes the creation of a heap by adjusting the elements of the array
            - Remove the root element of the heap repeatedly by shifting it to the end of the array
            - Store the heap structure with the remaining elements
        * What is the worst case time complexity for heap sort? Why?
            - O(n log n)
            - Occurs when the array elements are required to be sorted in reverse order
            - E.g. You have to sort in ascending order but its elements are in descending order

* **What is this code doing?**
    ```java
    void function(int arr[]) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - i - 1; j++)
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
    }
    ````
    * Keywords, concepts, or topics that should be in the response:
        * classic bubble sort example
        * Sorting the given array from least to greatest
    * Possible follow-up questions:
        * Why is the length of the second for loop n - i - 1? (J looks at j+1; would get an index out of bounds on last search)
        * What is the if statement doing? (swapping the value of j and j+1 if j is bigger)



### IMPORTANCE: REGULAR
[Back to top](#unit-java-data-structures-and-algorithims)

* **What is Insertion Sort?**
    * Keywords, concepts, or topics that should be in the response:
        - The array is split into a sorted and unsorted part, values from the unsorted part are picked and placed in the correct position in the sorted part
    * Possible follow-up questions:
        * What is the time complexity of Insertion Sort?
            - O(n<sup> 2 </sup>)

* **What is Selection Sort?**
    * Keywords, concepts, or topics that should be in the response:
        + We are repeatedly finding the minimum element from unsorted part and putting it at the beginning
        - We have 2 subarrays in 1 array
        - 1 subarray is sorted while the other remains unsorted
    * Possible follow-up questions:
        * What is the time complexity for Selection Sort?
            - O(n<sup>2</sup>)
        * What is a benefit of Selection Sort?
            - It never makes more than O(n) swaps
            - Useful when memory writes are a costly operation

* **Can you tell me the Time Complexity of this piece of code?**

    ```java
    public int fibo(int n) {
        System.out.println("Calling fibonaccis with input: " + n);
        if (n < 2) {
            return n;
        }
        return fibo(n-1) + fibo(n-2);
    }
    ```
    * Keywords, concepts, or topics that should be in the response:
        + Recursive solution, time complexity is O(2 <sup> n </sup>)
    * Possible follow-up questions:

* **What are Greedy Algorithms?**
    * Keywords, concepts, or topics that should be in the response:
        - Each small piece of the puzzle will provide an immediate output but generally does not consider the larger picture for the problem
        - Works recursively to construct a set of objects from the smallest possible pieces 
        - Mainly used for solving optimization problems
    * Possible follow-up questions:
        * What are some characteristics of Greedy Algorithms?
            - Creates 2 sets, one set contains all the chosen items, and another set contains the rejected items
            - Makes good local choices at every step in hope that the solution will either be feasible or optimal
        * What type of situations would Greedy Algorithms be used for? 
            - Used to find the shortest path
            - Used to find the minimum spanning tree using the prim's algorithm or the Kruskal's algorithm
            - Used to solve the fractional knapsack problem
        * What are some downsides of Greedy Algorithm?
            - Since it makes decisions based on the available information at each phase without considering the whole problem, there may be a possibility that the greedy solution does not yield the best solution for said problem

* **What is Divide and Conquer Algorithm?**
    * Keywords, concepts, or topics that should be in the response:
        - Has 3 parts:
        - Divide the problem into smaller bits
        - Solve the small bits recursively
        - Combine the small bits to get the final solution of the problem
    * Possible follow-up questions:
        * What algorithms follow the divide and conquer idea?
            - Quick sort
            - Merge sort

* **What is Breadth First Search?**
    * Keywords, concepts, or topics that should be in the response:
        - A graph traversal algorithm
        - Very similar to a binary tree
        - We use queue to traverse a graph
        - Put first node in queue
        - Repeatedly extracts nodes and put its neighbours in the queue
    * Possible follow-up questions:

* **What is Quick sort?**
    * Keywords, concepts, or topics that should be in the response:
        - Picks an element and places all the elements smaller than it on its left and the greater ones on the right then recursively sorts the 2 subarrays on the left and right of the element
    * Possible follow-up questions:

* **What is Kruskal's algorithm?**
    * Keywords, concepts, or topics that should be in the response:
        - Finds a minimum cost spanning trees using the greedy approach
        - Treats the graph as a forest and every node as an individual tree
        - One of the algorithms that fall under the greedy algorithm in graph theory
    * Possible follow-up questions:
        * How does Kruskal's algorithm work?
            - Sort all the edges based on weight from low to high
            - Take the edge with the lowest weight and add it to the spanning tree
            - If the edge that we are going to add creates a cycle, don't add it
            - Continue to add edges until we reach all the vertices
        * What are some real world applications of Kruskal's algorithm? 
            - LAN connections
            - Electrical wiring among cities