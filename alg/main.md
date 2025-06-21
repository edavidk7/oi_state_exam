# ALG

Status: Done

## Requirements

Základní algoritmy a datové struktury pro vyhledávání a řazení. Vyhledávací stromy, rozptylovací tabulky. Prohledávání grafu. Úlohy dynamického programování. Asymptotická
složitost a její určování.

• Řád růstu funkcí, asymptotická složitost algoritmu.

• Rekurze, Stromy, binární stromy, prohledávání s návratem.

• Fronta, zásobník, průchod stromem/grafem do šířky/hloubky.

• Binární vyhledávací stromy, AVL a B- stromy

• Algoritmy řazení: Insert Sort, Selection Sort, Bubble Sort, QuickSort Merge Sort, Halda, Heap
Sort, Radix sort, Counting Sort.

• Dynamické programování, struktura optimálního řešení, odstranění rekurze. Nejdelší společná podposloupnost, optimální násobení matic, problém batohu.

• Rozptylovací tabulky (Hashing), hashovací funkce, řešení kolizí, otevřené a zřetězené tabulky,
double hashing, srůstající tabulky, univerzální hashování.

## Function growth, asymptotic complexity

### Big O

![image.png](assets/image.png)

A function f is asymptotically bounded from the top by g if there exists a constant c, for which exists an x such that the c \* g(x) for any larger x is at least as high as f(x)

![image.png](assets/image%201.png)

### Big Omega

![image.png](assets/image%202.png)

A function f is asymptotically bounded from the bottom by g if there exists a constant c, for which exists an x such that the c \* g(x) for any larger x is at most as high as f(x)

### Big Theta

![image.png](assets/image%203.png)

Intersection of the two previous definitions

### Algorithm Complexity Classes

![image.png](assets/image%204.png)

![image.png](assets/image%205.png)

![image.png](assets/image%206.png)

### Recursion Complexity

Main idea: divide and conquer

Assembling a solution from sub-solutions

![image.png](assets/image%207.png)

How to compute the asymptotic complexity?

We can express the complexity for a given in from the recursive relationship

![image.png](assets/image%208.png)

### Substitution

![image.png](assets/image%209.png)

No optimal way how to guess the solution.

Example

![image.png](assets/image%2010.png)

![image.png](assets/image%2011.png)

### Recursive Tree Method

![image.png](assets/image%2012.png)

1. Add the tree leaves, we need to calculate the depth and width of the tree. Depth: log4(n). Width at the bottom (leaf count): 3^depth = 3^log4(n) = 4^log4(3)log4(n) = n^log4(3)
2. Add the constant term at every level of the tree: cn^2 + c*3*(n/4)^2 + c*3^2*(n/4)^2 + … is equivalent to a geometric series with q = 3/16. Compute the sum as 1/(1-q) = 16/13, so we get complexity of the nodes themselves at 16/13cn^2.
3. Now compare the complexity, since (16/13)cn^2 > n^log4(3), the algorithm is O(n^2)

![image.png](assets/image%2013.png)

![image.png](assets/image%2014.png)

## Trees

![image.png](assets/image%2015.png)

Additional properties:

- No cycles
- $|V| = |E|+1$

N-ary trees: every node has at most n-children

### Binary Trees

Regular: either 0 or 2 children

Balanced: All levels except for the last one are always full. For N-nodes, the depth can be estimated as ceil(log2(n+1))-1 (+1 for empty tree!)

![image.png](assets/image%2016.png)

There are multiple ways to perform depth-first binary tree traversal.

- Inorder: left → root → right
- Preorder: root → left → right
- Postorder: left → right → root

We can implement the recursive traversal using a stack (explicitly, not using the system stack).

Node counting:

![image.png](assets/image%2017.png)

Depth Calculation:

![image.png](assets/image%2018.png)

We can combine these and create a tree-drawing algorithm (y-axis depth, x-axis by the inorder index).

Longest path: maximum depth.

### Backtracking

![image.png](assets/image%2019.png)

![image.png](assets/image%2020.png)

Go through the state space tree, and test all possible solutions. If one is bad, return one level up and try a different one.

Can be very time consuming, is ideal to use pruning/heuristics/state space reduction.

## Graph Traversal

### Graph Representation

![image.png](assets/image%2021.png)

### BFS

Uses a queue, the neighbors of a node are added to the back, and a new node is taken from the front. This traverses the graph in a distance-order from the starting node. Never expands a node whose path length from the start is greater by 2 or more than the smallest node waiting in the queue.

![image.png](assets/image%2022.png)

We can implement it cyclically using an array.

Complexity: O(V+E) for an adjacency list and hashset visitation map

### DFS

Uses a stack, the neighbors of a node are pushed onto the stack and the next node to be explored is popped from the stack → traverses in depth first.

We can use the system stack (recursive function) or an explicit stack structure.

Complexity: O(V+E) for an adjacency list and hashset visitation map

### Toposort

In a DAG, iteratively take away the nodes with zero incoming degree, building an order of the nodes that ensures no unresolved dependency in previous steps.

## Search

### Search in an ordered array

Binary search

Simple idea, given some target element, we can look left/right to see how far we are and quickly reduce the search space.

Interpolation search

Based on the first and last element, estimate the index of the query through a linear function. Then halve the interval like in binsearch and repeat. Requires the data to be uniformly distributed, will degrade to linear complexity with large outliers

Exponential search

Incrementally look at exponentially further away numbers until the interval is reduced. Then binsearch in this interval. Data-dependent time complexity.

### Binary Search Tree

Left child: always lower than root

Right child: always higher than root

Tiebreakers up to design decision.

Inorder traversal gives an ordered array.

Find:

![image.png](assets/image%2023.png)

Insert:

![image.png](assets/image%2024.png)

Delete:

On leaves: simple

If a node has one child:

![image.png](assets/image%2025.png)

![image.png](assets/image%2026.png)

If a node has two children: must perform a rotation

![image.png](assets/image%2027.png)

![image.png](assets/image%2028.png)

![image.png](assets/image%2029.png)

### AVL Tree

![image.png](assets/image%2030.png)

Insertion: we have to take care of a potential break in balance using a rotation. The rotation de-facto adjusts the depths such that the invariant holds.

![image.png](assets/image%2031.png)

![image.png](assets/image%2032.png)

![image.png](assets/image%2033.png)

![image.png](assets/image%2034.png)

![image.png](assets/image%2035.png)

Similarly for the LR rotation. This helps balance out the tree if we get a depth disparity larger than 1.

Rule of thumb:

- Suppose we delete/insert a node, and traverse upwards the tree
- Once we encounter a unbalanced node, remember 2 last directions we came from (Left/Right)
- If its LL/RR, perform a simple single L or R rotation. If its RL or LR, perform those rotations.

Deletion:

After deleting a node, traverse upwards, update balances, and if unbalanced, update using the two edges towards the deepest subtree of the unbalanced node. We will have to rebalance in every node. That gets out of balance.

![image.png](assets/image%2036.png)

### B-Tree

Database systems, filesystems

![image.png](assets/image%2037.png)

Find:

![image.png](assets/image%2038.png)

Insert:

![image.png](assets/image%2039.png)

1. Traverse the tree
2. Find the last suitable child
3. If can insert into remaining space, great
4. If out of capacity, median-sort the contents along with new element (robust splitting for balancing), pick the median value, and split along this value into 2 children. Push the median upstream, along with these two children (left and right). If the root cannot fit the median, repeat the whole procedure recursively

The tree grows upwards, the root changes.

Delete:

![image.png](assets/image%2040.png)

![image.png](assets/image%2041.png)

1. Traverse the tree
2. If the node is in a full leaf, easy, delete it
3. If the node has multiple children, use the same approach as in BST, and replace with the nearest smallest or largest
4. If the node is in an almost empty leaf, and removing it would violate the minimum k-element invariant, have to look in to neighbors → merge the current leaf, parent value (not node) and neighbor, sort, take median, and split again
5. If we perform 4., but the neighbors are too empty, we will have enough nodes after merging to cover exactly one full leaf. Once we do that, the parent now does not have enough values, we can iterate this approach upwards towards the root. Empty nodes will get deleted (except for root, it can have at minimum 1 element)

## Sorting

### Selection Sort

![image.png](assets/image%2042.png)

For each position in the array, look for the smallest element ahead, and swap it with the current position. For every position, we select the ideal element.

### Insertion Sort

![image.png](assets/image%2043.png)

Traverse each position, take its element, and insert it into the correct place between the preceding positions. If we pick e[i], then for all j=0..i-1, starting at i-1, compare the value e[j] and e[i]. If e[i] is smaller, swap them. This eventually inserts the element in the right position.

### Bubble Sort

![image.png](assets/image%2044.png)

![image.png](assets/image%2045.png)

For each position, starting at i=0, bubble up the elements by pairwise comparison (push larger more towards the end).

![image.png](assets/image%2046.png)

### Quicksort

Divide and conquer recursive approach.

Main idea: split the array into two parts, one smaller and one larger.

How? Pick a splitting element, so called pivot.

Then take two pointers, one at the beginning or the array, one at the end.

Compare the elements at pointer positions, if we find an offending pair (upper half but less than pivot/lower half but higher than pivot), swap the values at those positions. Every pointer moves unless we find a mutually-offending pair.

![image.png](assets/image%2047.png)

![image.png](assets/image%2048.png)

No balance guarantees → very bad worst case.

![image.png](assets/image%2049.png)

### Stable Sorting

Does not affect the order of comparable elements (in some sense equal) from input to output.

![image.png](assets/image%2050.png)

### Merge Sort

Main idea: merge two sorted arrays in a way that does not violate the sorting

![image.png](assets/image%2051.png)

Merge Operation

![image.png](assets/image%2052.png)

2 riders approach, at output[i], place whichever element is smallest from the other two.

![image.png](assets/image%2053.png)

Improve performance by sharing the arrays and sorting elements in-place, always needs one output and one source (independent).

![image.png](assets/image%2054.png)

Is also stable (very nice!).

### Heap

A binary tree with an ordering rule. It remains a balanced binary tree.

![image.png](assets/image%2055.png)

We can store it efficiently using an array with a simple indexing rule.

![image.png](assets/image%2056.png)

Pop rule:

1. Remove root, place the last element in its place, now the heap property is violated
2. Look at the children, pick the smaller one and swap the root with this smaller child
3. Recur downwards until the heap is fixed.

Every subheap of a heap is a valid heap.

We can use heap to sort an array:

![image.png](assets/image%2057.png)

When building a heap, because of the recursive property, we can start by constructing the smallest lower heaps and continuing upwards, then we’re certain we don’t violate the already built heap. Also observation: the source array has to be explored only up to its half, as the rest are simply leaves.

We can use heap as a priority queue, the insertion is implemented by appending an element at the bottom and letting it “bubble” up. Or a more efficient approach, Look at the spot where it would be inserted, check the elements along the path towards the root, shift them down and then directly insert A

### Radix Sort

On strings or numbers (number is a decimal string): For all possible characters in the string, sort them lexicographically, by utilizing per-character counting bins (radix).

![image.png](assets/image%2058.png)

![image.png](assets/image%2059.png)

![image.png](assets/image%2060.png)

When going one character up, we need to create a new sorting link structure. We do this by traversing the link structures from the previous step, and incrementally updating the new link structure for the respective characters (e.g. table for c2 from link structure of c3). This ensures that the order in which elements are inserted into the c2 link structure is the stable sorted one from previous step (because we start with the lowest letter first).

![image.png](assets/image%2061.png)

### Counting Sort

If we have some elements with a known bounded range that are categorical, we can create a counting table (number of each of the elements), and re-distribute them in an ordered manner:

![image.png](assets/image%2062.png)

Second, compute the prefix sum of the counting table, this will give us the starting indices

![image.png](assets/image%2063.png)

Now, for each input element, place it in its respective index from the calculated range, which is slowly decremented.

![image.png](assets/image%2064.png)

## Dynamic Programming

Used to search for optimal solutions of problems:

![image.png](assets/image%2065.png)

![image.png](assets/image%2066.png)

### Tabelization

For often repeating results, we can cache them in a table to be retrieved whenever they’re needed in the future.

![image.png](assets/image%2067.png)

### Longest Path in a DAG

![image.png](assets/image%2068.png)

![image.png](assets/image%2069.png)

First, sort the DAG topologically to get a clear processing order. Then, go through the DAG in the topo order, processing each node.

![image.png](assets/image%2070.png)

![image.png](assets/image%2071.png)

### Longest Common Subsequence

![image.png](assets/image%2072.png)

We have 2 sequences, and want to know the longest common subsequence. Given a shorter common subsequence, we can derive a rule on how to build it logically. That is, we connect the same letter with the previously longest subsequence. Also observe something simple - for n=1 and m=any (and vice versa), the LCS is simply the letter equality. This is enough to get us started on the DP.

![image.png](assets/image%2073.png)

![image.png](assets/image%2074.png)

For all subsequence combinations of the 2 input sequences, we can find the LCS using the previously derived rules in the table.

### Longest Increasing Subsequence

Inspire from the longest path in a DAG → an edge exists between 2 numbers if theyre larger or equal (5 → 6)

We don’t have to build the DAG explicitly, we can process the values one-by-one.

![image.png](assets/image%2075.png)

![image.png](assets/image%2076.png)

1. Length 1: value 4 at index 1
2. Length 1: update the value to 3, it is a lower number, it cannot make it any worse
3. Length 2: 8 is larger than 3, d = 1, therefore add a sequence of length 2 ending at k=3, previous=2
4. Length 3: 10 is larger than 8, d = 2, add a sequence of length 3, currently ending at index 4 (remember, iL is indexed by sequence length)

…

### Optimal Matrix Multiplication

![image.png](assets/image%2077.png)

![image.png](assets/image%2078.png)

We will construct a DP table for each subterm.

![image.png](assets/image%2079.png)

![image.png](assets/image%2080.png)

![image.png](assets/image%2081.png)

![image.png](assets/image%2082.png)

![image.png](assets/image%2083.png)

### Knapsack

![image.png](assets/image%2084.png)

The unlimited version

![image.png](assets/image%2085.png)

Idea: The ideal combination of elements in the knapsack is the same as taking a smaller-capacity knapsack and adding the “best” item.

This is the longest path in a DAG.

![image.png](assets/image%2086.png)

0/1 limited knapsack

![image.png](assets/image%2087.png)

![image.png](assets/image%2088.png)

We can create a cartesian product between all sets and all capacities, and we will iteratively find which set/capacity combination gives us the best result. When iterating over sets, we can choose whether we want to include the object or not (0/1).

![image.png](assets/image%2089.png)

![image.png](assets/image%2090.png)

Simply put, for each x and capacity, look whether it makes sense to include the item or not, and pick the better option.

It can be also formulate as a longest path in a DAG:

![image.png](assets/image%2091.png)

It coincides with the tabular approach:

![image.png](assets/image%2092.png)

## Hashing

![image.png](assets/image%2093.png)

![image.png](assets/image%2094.png)

![image.png](assets/image%2095.png)

![image.png](assets/image%2096.png)

![image.png](assets/image%2097.png)

### Hashing function examples

![image.png](assets/image%2098.png)

![image.png](assets/image%2099.png)

![image.png](assets/image%20100.png)

![image.png](assets/image%20101.png)

### Collision Resolution

Linked data structures

![image.png](assets/image%20102.png)

![image.png](assets/image%20103.png)

Open-Address hashing

- We know roughly the amount of elements
- Avoids pointers
- Fixed hash table

![image.png](assets/image%20104.png)

![image.png](assets/image%20105.png)

![image.png](assets/image%20106.png)

Linear Probing

![image.png](assets/image%20107.png)

![image.png](assets/image%20108.png)

Double Hashing:

![image.png](assets/image%20109.png)

i is the current index filled with some element

### Coalesced Hashing

![image.png](assets/image%20110.png)

LISCH

![image.png](assets/image%20111.png)

![image.png](assets/image%20112.png)

EISCH

![image.png](assets/image%20113.png)

![image.png](assets/image%20114.png)

With auxiliary memory

LICH - same as LISCH, but uses the cellar, and cellar is not addressed by h(k)

Same for EICH

VICH performs LICH for items that fit in the cellar and EISCH once cellar runs out
