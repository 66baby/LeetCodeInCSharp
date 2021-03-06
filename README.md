# LeetCodeInCSharp

# List
+ #12 Integer to roman
+ #13 Roman To Integer
+ #28 Implement strStr()
+ #35 Search insert position
+ #53 Maximun Subarray
+ #66 Plus One
+ #70 Climbing stairs
+ #83 Remove duplicates from sorted list
+ #94 Binary tree in-order traversal
+ #96 Unique binary search trees
+ #100 Same tree
+ #104 Maximum depth of a binary tree
+ #107 Level order binary tree traversal II
+ #116 Populating next right pointers in each node
+ #122 Best Time to Buy and Sell Stock II
+ #136 Single number
+ #137 Single number II
+ #141 Linked list cycle
+ #144 Binary tree pre-order traversal
+ #168 ExcelSheetColumnTitle
+ #169 Majority element
+ #191 Number of 1 bits
+ #217 Contains duplicate
+ #226 Invert binary tree
+ #235 Lowest Common Ancestor of a Binary Search Tree
+ #237 Delete node in a linked list
+ #238 Product of array except self
+ #242 Valid anagram
+ #258 Add digits
+ #260 Single number III
+ #268 Missing number
+ #283 Move Zeroes
+ #292 Nim Game

# Detail
## #12 Integer to roman
**LeetCode Link**:  
[https://leetcode.com/problems/integer-to-roman/](https://leetcode.com/problems/integer-to-roman/)  
**Problem description**:  
Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/12_IntegerToRoman.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/12_IntegerToRoman.cs)  
**Detail**:  
-my solution:  
Very straight forward solution.
```
            var dic1 = new Dictionary<int, string> { { 1, "I" }, { 2, "II" }, { 3, "III" }, { 4, "IV" }, { 5, "V" }, { 6, "VI" }, { 7, "VII" }, { 8, "VIII" }, { 9, "IX" }, { 0, "" } };
            var dic10 = new Dictionary<int, string> { { 1, "X" }, { 2, "XX" }, { 3, "XXX" }, { 4, "XL" }, { 5, "L" }, { 6, "LX" }, { 7, "LXX" }, { 8, "LXXX" }, { 9, "XC" }, { 0, "" } };
            var dic100 = new Dictionary<int, string> { { 1, "C" }, { 2, "CC" }, { 3, "CCC" }, { 4, "CD" }, { 5, "D" }, { 6, "DC" }, { 7, "DCC" }, { 8, "DCCC" }, { 9, "CM" }, { 0, "" } };
            var dic1000 = new Dictionary<int, string> { { 1, "M" }, { 2, "MM" }, { 3, "MMM" }, { 0, "" } };
            return dic1000[num / 1000 % 10] + dic100[num / 100 % 10] + dic10[num / 10 % 10] + dic1[num % 10];
```
-the smarter solution, [refer to lucifer27's solution](https://leetcode.com/discuss/49870/my-java-solution-easy-to-understand):  This is slower (O(N) or O(1)???since num has a upper limit???)
```
            int[] values = { 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 };
            string[] strs = { "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I" };
            string roman = "";
            for (int i = 0; i < values.Length; i++)
            {
                while (num >= values[i])
                {
                    num -= values[i];
                    roman += strs[i];
                }
            }
            return roman;
```

## #13 Roman To Integer
**LeetCode Link**:  
[https://leetcode.com/problems/roman-to-integer/](https://leetcode.com/problems/roman-to-integer/)  
**Problem description**:  
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/13_RomanToInteger.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/13_RomanToInteger.cs)  
**Detail**:  
-O(N) solution:
The special notation combinations in Roman numerals are ```4:IV, 9:IX, 40:XL, 90:XC, 400:CD, 900:CM```, other than that, all notations are just added together. For this solution, iterate through the whole string, once meet a specific combination list above, move the iterator forward once more. Although this method takes to many lines, its worst case time complexity is only O(N), and it does not need extra space.

## #28 Implement strStr()
**LeetCode Link**:  
[https://leetcode.com/problems/implement-strstr/](https://leetcode.com/problems/implement-strstr/)  
**Problem description**:  
Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/28_ImplementStrStr.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/28_ImplementStrStr.cs)  
**Explanation**:  
- Naive string search (136ms):  
Iterate through the ```haystack``` char by char, if the char matches the first char in ```needle```, iterate through the following chars in the ```haystack``` with the length of ```needle``` to check match. This brute force search has time complexity of O(MN).  
- Rabin-karp algorithm (132ms):  
(To be solved!!)Solution passed LeetCode test, but still confusing about the 'base' choice. Has asked on StackOverFlow.  
[[StackOverFlowLink]](http://stackoverflow.com/questions/32576677/issue-with-implementing-rabin-karp-algorithm-to-search-string-in-leetcode-28-im)  
- KMP algorithm:  
...to be implemented...
- Boyer- Moore algorithm:  
...to be implemented...

## #35 Search insert position
**LeetCode Link**:  
[https://leetcode.com/problems/search-insert-position/](https://leetcode.com/problems/search-insert-position/)  
**Problem description**:  
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order. You may assume no duplicates in the array. Here are few examples.
```
[1,3,5,6], 5 → 2
[1,3,5,6], 2 → 1
[1,3,5,6], 7 → 4
[1,3,5,6], 0 → 0
```
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/35_SearchInsertPosition.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/35_SearchInsertPosition.cs)  
**Explanation**:  
- Linear search solution (Time: O(n), 164ms): 
```
for (int i = 0; i < nums.Length; i++)
    if (target <= nums[i]) return i;
return nums.Length;
```
- Binary search solution (Time: O(log(n)), 156ms):  
Loop until ```low == high```(return exact match if there is), if```target > nums[high]```, return ```high + 1```, else return ```high```.

## #53 Maximun Subarray
**LeetCode Link**:  
[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)  
**Problem description**:  
Find the contiguous subarray within an array (containing at least one number) which has the largest sum. For example, given the array [−2,1,−3,4,−1,2,1,−5,4], the contiguous subarray [4,−1,2,1] has the largest sum = 6.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/53_MaximumSubarray.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/53_MaximumSubarray.cs)  
**Detail**:  
-O(n) solution (156ms), refer to [xi11's solution](https://leetcode.com/discuss/38913/o-n-time-o-1-space-dp-solution-java)  
Assuming we have a abstract dynamic window, this window start from 0th item with 1 length. Declare a ```max``` to store current maximum sum, a ```prev``` to store latest iterated window's sum, a ```cur``` to store current window's sum, they are all initialized to ```nums[0]```. Iterate through nums, if ```prev``` is positive, previous window is worth adding to current item, thus the window expand to current item, the current sum ```cur``` equal to previous sum + current item ```cur = prev + nums[i]```; if prev is negative, it is not worth adding to current item, the life of old window ends, start a new window begin from current item, update current sum ```cur``` to current item ```nums[i]```'s value. ```max``` is independent with this windowing process, only that every time current sum ```cur``` changes, compare with old ```max``` and update ```max``` to ```Math.Max(max,cur)```.

## #66 Plus One
**LeetCode Link**:  
[https://leetcode.com/problems/plus-one/](https://leetcode.com/problems/plus-one/)  
**Problem description**:  
Given a non-negative number represented as an array of digits, plus one to the number. 
The digits are stored such that the most significant digit is at the head of the list.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/66_PlusOne.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/66_PlusOne.cs)  
**Explanation**:  
- Simple iteration solution(500ms):  
Iterate through ```digits```, from ```digits[digits.Length - 1]``` to ```digits[0]```. If current number is not 9, the loop is not worth continueing, thus just add ```1``` to it and break the loop, and return ```digits```; otherwise make current number ```0``` and continue. If nothing's returned after the loop, it means all digits are ```9```, thus create a new int array ```newDigits``` with ```Length = digits.Length + 1```, set ```newDigits[0]``` to ```1```, and return ```newDigits```.

## #70 Climbing stairs
**LeetCode Link**:  
[https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)  
**Problem description**:  
You are climbing a stair case. It takes n steps to reach to the top.
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/70_ClimbingStairs.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/70_ClimbingStairs.cs)  
**Explanation**:  
- Fabonacci solution:  
for ```n = 1 : ...```, the result would be ```1, 2, 3, 5, 8, 13, 21, 34, 55```, thus you can see it is a Fabonacci sequence. Except the first 2 numbers, every number equal to: ```number[i] = number[i-2] + number[i-1]```.

## #83 remove duplicates from sorted list
**LeetCode Link**:  
[https://leetcode.com/problems/remove-duplicates-from-sorted-list/](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)  
**Problem description**:  
Given a sorted linked list, delete all duplicates such that each element appear only once.  
For example,  
Given 1->1->2, return 1->2.  
Given 1->1->2->3->3, return 1->2->3.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/83_RemoveDuplicatesFromSortedList.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/83_RemoveDuplicatesFromSortedList.cs)  
**Explanation**:  
- common solution:  
if ```current.val == current.next.val```, ```current.next = current.next.next```.  

## #94 Binary tree in-order traversal
**LeetCode Link**:  
[https://leetcode.com/problems/binary-tree-inorder-traversal/](https://leetcode.com/problems/binary-tree-inorder-traversal/)  
**Problem description**:  
Given a binary tree, return the inorder traversal of its nodes' values. Note: Recursive solution is trivial, could you do it iteratively?  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/94_BinaryTreeInOrderTraversal.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/94_BinaryTreeInOrderTraversal.cs)  
**Explanation**:  
- Recursive way (524ms):  
```
method inorder(root){
    inorder(root.left);
    store root;
    inorder(root.right);
}
```
- Stack solution:  
This is an iteration solution via stack. 
```
        root
        /\
       /\
      /\
      subtree1
       /
      /\
      subtree2
       /
      /
```
It treats every right child as a start of a subtree. It stores a subtree in stack, deals with it, and then track back to the latest node with right node, and goes into this subtree and deal with it. Well this is hard to explain clearly :(.
- Morris traversal  
Seems to be the best iteration solution, to be implemented.

## #96 Unique binary search trees
**LeetCode Link**:  
[https://leetcode.com/problems/unique-binary-search-trees/](https://leetcode.com/problems/unique-binary-search-trees/)  
**Problem description**:  
Given n, how many structurally unique BST's (binary search trees) that store values 1...n?  
For example, Given n = 3, there are a total of 5 unique BST's.
```
   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/96_UniqueBinarySearchTrees.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/96_UniqueBinarySearchTrees.cs)  
**Detail**:  
- Iteration way(52ms), refer to [rain4's solution](https://leetcode.com/discuss/55761/c%23-accepted-52ms-based-on-the-quora-answer) and [Mohit modi's explanation](https://www.quora.com/Given-n-how-many-structurally-unique-BSTs-binary-search-trees-that-store-values-1-to-n-are-there):  
    + For different root choice, you can always devide the BST into left-sub-BST and right-sub-BST. Recursively for each sub-BST we can devide it into 2 sub-BSTs.
    + For different root choice:  
        1. root == 1, 0 element on the left, n - 1 element on the right
        2. root == 2, 1 element on the left, n - 2 element on the right
        3. root == 3, 2 element on the left, n - 3 element on the right
        4. ...
        5. root == i, i - 1 element on the left, n - i element on the right
        6. ...
        7. root == n, n - 1 element on the left, 0 element on the right
    + For a BST of n nodes, we want to count all the possible root choices, thus let sum(n) represent the result, we have:  
        ```sum(n) = sum(0)sum(n - 1) + sum(1)sum(n - 2) + sum(2)sum(n - 3) + ... + sum(i - 1)sum(n - i) + ... + sum(n - 1)sum(0)```
    + Declare an array to store sum(1) to sum(n), although what we want is just sum(n), we still need to find out and store sum(1) to sum(n), because each sum is used by the next sum. To visualize each turn:  
        1. ```sum(1) = 1``` for a BST with only 1 node, there is only 1 possible outcome.
        2. ```sum(2) = sum(0)sum(1) + sum(1)sum(0) = 1 + 1 = 2``` sum(1) is acquired from above.
        3. ```sum(3) = sum(0)sum(2) + sum(1)sum(1) + sum(2)sum(0) = 2 + 1 + 2 = 5```
        4. ...  
    At the end, we will get sum(n).

## #100 Same tree
**LeetCode Link**:  
[https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)  
**Problem description**:  
Given two binary trees, write a function to check if they are equal or not. 
Two binary trees are considered equal if they are structurally identical and the nodes have the same value.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/100_SameTree.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/100_SameTree.cs)  
**Explanation**:  
- Recursive way (160ms):  
A very straightforward one line recursive solution. 4 cases:  
both null -> true;  
one is null but the other is not -> false;  
both not null but value not equal -> false;  
else -> check children;  

## #104 Maximum depth of a binary tree
**LeetCode Link**:  
[https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)  
**Problem description**:  
Given a binary tree, find its maximum depth.  
**Source code**: [https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/104_MaximumDepthOfABinaryTree.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/104_MaximumDepthOfABinaryTree.cs)  
**Explanation**:  
- Recursive way (164ms):  
A very straightforward one line recursive solution.

## #107 Level order binary tree traversal II  
**LeetCode Link**:  
[https://leetcode.com/problems/binary-tree-level-order-traversal-ii/](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)  
**Problem description**:  
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/107_LevelOrderBinaryTreeTraversalII.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/107_LevelOrderBinaryTreeTraversalII.cs)  
**Explanation**:  
- BFS solution (502ms):  
Use a queue to do Breadth First Search. The way I did to check the level is creating a class called NodeWithHeight to wrap the TreeNode and a Height property. So every time instead of enqueueing a node into the queue, I wrap it and its height in a NodeWithHeight object, and  enqueue this object to the queue.  

## #116 Populating next right pointers in each node
**LeetCode Link**:  
[https://leetcode.com/problems/populating-next-right-pointers-in-each-node/](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)  
**Problem description**:  
Given a binary tree:  
```
    struct TreeLinkNode {
        TreeLinkNode *left;
        TreeLinkNode *right;
        TreeLinkNode *next;
    }
```
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL. Initially, all next pointers are set to NULL. Note: You may only use constant extra space; You may assume that it is a perfect binary tree (ie, all leaves are at the same level, and every parent has two children).  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/116_PopulatingNextRightPointersInEachNode.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/116_PopulatingNextRightPointersInEachNode.cs)  
**Explanation**:  
- BFS queue solution and DFS recursive solution (200ms):  
Both ways are straight forward. The simple logic they both use are:  
```
if(root.left != null) root.left.next = root.right;
if(root.right != null && root.next != null) root.right.next = root.next.left;
```

## #122 Best time to buy and sell stack II
**LeetCode Link**:  
[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)  
**Problem description**:  
Say you have an array for which the ith element is the price of a given stock on day i.  
Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/122_BestTimeToBuyAndSellStockII.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/122_BestTimeToBuyAndSellStockII.cs)  
**Explanation**:  
- Iteration way (148ms):  
The problem description is confusing. Actually what it says is to find the maximum profit per share of a stock. Just buy at low price day (compare to day + 1) and sell at (day + 1);

## #136 Single number
**LeetCode Link**:  
[https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)  
**Problem description**:  
Given an array of integers, every element appears 
twice except for one. Find that single one.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/136_SingleNumber.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/136_SingleNumber.cs)  
**Detail**:  
- Bitwise XOR (156ms, O(n)):  
This solution uses 'bitwise XOR' to quickly solve the problem, each element in the array only needs to be checked once.
```^``` is the bitwise XOR in C#. For bitwise XOR: (0 XOR 0 = 0, 0 XOR 1 = 1, 1 XOR 0 = 1, 1 XOR 1 = 0). Thus the ones are not single will offset each other, only the single number will live to the end.

## #137 Single number II
**LeetCode Link**:  
[https://leetcode.com/problems/single-number-ii/](https://leetcode.com/problems/single-number-ii/)  
**Problem description**:  
Given an array of integers, every element appears three times except for one. Find that single one.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/137_SingleNumberII.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/137_SingleNumberII.cs)  
**Explanation**:  
- Dictionary solution (152ms):  
Declare a ```Dictionary<int , int>```, iterate through ```nums```, add a new ```KeyValuePair``` which ```key``` is current ```num``` and ```value``` is ```1``` to it if the number is met in the first time, or ```value ++``` if the key already exists. Then iterate through the dictionary to find the one with ```value == 1```.

## #141 Linked list cycle
**LeetCode Link**:  
[https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)  
**Problem description**:  
Given a linked list, determine if it has a cycle in it. Follow up: Can you solve it without using extra space?  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/141_LinkedListCycle.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/141_LinkedListCycle.cs)  
**Explanation**:  
- Best way so far (156mms), refer to [[huxijiuhao's solution]](https://leetcode.com/discuss/54343/simple-and-easy-understanding-java-solution-time-n-space-o-1):  
The key to solve this problem is to find a way to track all visited nodes. Recording them causes extra space, the simpler way is to give all visited nodes an uniform feature. "huxijiuhao"'s solution modify all visited nodes' ```next``` pointer points to the ```head```, so during the traversal once you have node points to any of the nodes you visited, it will point to the ```head```. The time complexity is O(n), and space is O(1). (This solution breaks the linked list, but the question does not have any consideration on this, so this is all good)

## #144 Binary tree pre-order traversal
**LeetCode Link**:  
[https://leetcode.com/problems/binary-tree-preorder-traversal/](https://leetcode.com/problems/binary-tree-preorder-traversal/)  
**Problem description**:  
Given a binary tree, return the preorder traversal of its nodes' values. Note: Recursive solution is trivial, could you do it iteratively?  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/144_BinaryTreePreOrderTraversal.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/144_BinaryTreePreOrderTraversal.cs)  
**Explanation**:  
- Recursion way (508ms):  
```
method preorder(root){
    store root;
    preorder(root.left);
    preorder(root.right);
}
```
- Stack solution (520ms):  
```
method preorder(root){
    stack.push(root);
    while(stack not empty){
        temp = stack.pop;
        list.add(temp);
        stack.push(temp.right);
        stack.push(temp.left);
    }
    return list;
}
```

## #168 Excel sheet column title
**LeetCode Link**:  
[https://leetcode.com/problems/excel-sheet-column-title/](https://leetcode.com/problems/excel-sheet-column-title/)  
**Problem description**:  
Given a positive integer, return its corresponding column title as appear in an Excel sheet.  
```  
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
```  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/168_ExcelSheetColumnTitle.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/168_ExcelSheetColumnTitle.cs)  
**Explanation**:  
- Modulo solution (48ms):  
This problemm is actually converting a ```0``` started 10-scale system to a ```1``` started 26-scale system.  
```number % 26``` gives a remainder to map character. ```'A'``` is #65 in the ASCII table. Thus use ```remainder + 65``` to map character in the ASCII table. 
Because ```26 % 26``` leads to 0 which cannot used to map ```'Z'```, I used '0 - 25' instead of '1 - 26' to map 'A - Z'.
Thus in every execution in the loop, do ```n--;``` at the begining.

## #169 Majority element
**LeetCode Link**:  
[https://leetcode.com/problems/majority-element/](https://leetcode.com/problems/majority-element/)  
**Problem description**:  
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times. You may assume that the array is non-empty and the majority element always exist in the array.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/169_MajorityElement.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/169_MajorityElement.cs)  
**Explanation**:  
- Sorting 2-line solution (152ms):  
Sort the array first, no matter if the majority items are larger or small, simply pick the item in the middle ((n/2 + 1)th item if even numbers). Since the C# ```Array.Sort()``` uses quicksort algorithm, the time complexity would be O(nlogn).  
- Iteration solution (152ms), refer to [[andy-sheng's solution]](https://leetcode.com/discuss/45660/my-o-n-time-and-o-1-space-solution-in-c)  
This method provides O(n) time complexity.

## #171 Excel sheet column number
**LeetCode Link**:  
[https://leetcode.com/problems/excel-sheet-column-number/](https://leetcode.com/problems/excel-sheet-column-number/)  
**Problem description**:  
Given a column title as appear in an Excel sheet, return its corresponding column number.
```  
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
```  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/171_ExcelSheetColumnNumber.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/171_ExcelSheetColumnNumber.cs)  
**Explanation**:  
- Common way (164ms):  
Split string into charArray, iterate through, each item times corresbonding 26's power and add to the sum.

## #191 Number of 1 bits
**LeetCode Link**:  
[https://leetcode.com/problems/number-of-1-bits/](https://leetcode.com/problems/number-of-1-bits/)  
**Problem description**:  
Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).
For example, the 32-bit integer '11' has binary representation 00000000000000000000000000001011, so the function should return 3.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/191_NumberOf1Bits.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/191_NumberOf1Bits.cs)  
**Explanation**:  
- Bitwise shift and modulo (56ms):  
do ```n % 2```, will actually return the LSB of n in binary. Add this value to the result, and shift ```n``` 1 bit to the right. Loop until ```n``` equals 0.

## #217 Contains duplicate
**LeetCode Link**:  
[https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)  
**Problem description**:  
Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/217_ContainsDuplicate.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/217_ContainsDuplicate.cs)  
**Explanation**:  
- Via hashset solution (O(n), 176ms):  
In C# .NET, 2 features of Hashset<type> are used this problem. 1st, each element in a hashset is unique, duplicate adding will return false; 2nd, the searching time complexity is O(1), thus the adding time complexity is O(1). To solve this problem, declare a ```Hashset<int> hashset```, iterate through the given ```nums``` and add each item to ```hashset```, return true if ```hashset.Add()``` returns false.   

## #226 Invert binary tree
**LeetCode Link**:  
[https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)  
**Problem description**:  
Invert a binary tree.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/226_InvertBinaryTree.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/226_InvertBinaryTree.cs)  
**Explanation**:  
- Recursive way (160ms):
Feel sorry for Max Howell. I might get nervous too.

## #235 Lowest Common Ancestor of a Binary Search Tree
**LeetCode Link**:  
[https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)  
**Problem description**:  
Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/235_LowestCommonAncestorOfABinarySearchTree.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/235_LowestCommonAncestorOfABinarySearchTree.cs)  
**Explanation**:  
- traversal solution(188ms):  
To find the lowest common ancestor, it is actually looking for the first node that match the conditions that both (<=) than the small node and (>=) than the large node at the same time.

## #237 Delete node in a linked list
**LeetCode Link**:  
[https://leetcode.com/problems/delete-node-in-a-linked-list/](https://leetcode.com/problems/delete-node-in-a-linked-list/)  
**Problem description**:  
Write a function to delete a node (except the tail) 
in a singly linked list, given only access to that node. 
Supposed the linked list is 1 -> 2 -> 3 -> 4 and you 
are given the third node with value 3, the linked list 
should become 1 -> 2 -> 4 after calling your function.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/237_DeleteNodeInALinkedList.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/237_DeleteNodeInALinkedList.cs)  
**Explanation**:  
- 2 line solution(172ms):  
The list pointer is not provided, thus you cannot iterate through the list, and you are not given the previous ```next``` pointer. This problem needs an alternative way to delete the node.  
```... ---> currentNodeToBeDeleted(node 0) ---> node1 ---> node2 ---> ...```  
To delete node0, copy the value of node1 to node0, change node0's ```next``` to point to node2.  
Thus node0 now holds the properties of node1, and the node actually being discarded on the memory is node1.

## #238 Product of array except self
**LeetCode Link**:  
[https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)  
**Problem description**:  
Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i]. Solve it without division and in O(n). For example, given [1,2,3,4], return [24,12,8,6]. Follow up: Could you solve it with constant space complexity? (Note: The output array does not count as extra space for the purpose of space complexity analysis.)  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/238_ProductofArrayExceptSelf.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/238_ProductofArrayExceptSelf.cs)  
**Explanation**:  
- The best solution so far (512ms), refer to [[areshead's solution]](https://leetcode.com/discuss/53781/my-solution-beats-100%25-java-solutions)  :
What it does is to iterate through the ```nums``` array twice. Firstly set ```pre``` and ```post``` to 1, they are the product before ```(i)th``` item and product after ```(i)th``` item. In the first loop, iterate through ```nums``` incrementally, set ```result[i]``` to ```pre``` and then update the ```pre``` by ```pre *= nums[i]```. In the second loop, iterate through ```nums``` decrementally, update ```result[i]``` by ```result[i] *= post``` and then update ```post``` by ```post *= nums[i]```.  

## #242 Valid anagram
**LeekCode Link**:  
[https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)  
**Problem description**:  
Given two strings s and t, write a function to determine if t is an anagram of s.  
For example,  
s = "anagram", t = "nagaram", return true.  
s = "rat", t = "car", return false.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/242_ValidAnagram.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/242_ValidAnagram.cs)  
**Detail**:  
- sorting solution:  
Alphabetically sort each string, and commpare them. This method is relatively slow, each sorting (quick sort) has O(nlogn) time complexity.To sort a string:  
```
char[] a = s.ToCharArray();
Array.Sort(a);
return new string(a);
```

- an O(n) solution (132ms), refer to [零一's solution](https://leetcode.com/discuss/57355/0ms-c-solution-o-n-time):  
Declare an int array ```alphabet``` with 26 Length, that each one related to an character in the alphabet table.  Iterate through the 1st string, ++ the value at the corresbonding slot in ```alphabet```, then iterate through the 2nd string, -- the value at the corresbonding slot in ```alphabet```, after this, if the value of each slot in ```alphabet``` is 0, then return true, otherwise return false.


## #258 Add digits
**LeekCode Link**:  
[https://leetcode.com/problems/add-digits/](https://leetcode.com/problems/add-digits/)  
**Problem description**:  
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit. 
For example: given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/258_AddDigits.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/258_AddDigits.cs)  
**Explanation**:  
- The best solution with O(1) time complexity:  
[[Wikipedia reference]](https://en.wikipedia.org/wiki/Digital_root)  
In short words, "If a number produces a digital root of exactly 9, then the number is a multiple of 9."  
```result = num - root((num - 1) / 9) * 9;```  
- Recursive way(68ms):  
Return the num if num < 10, else just calculate the sum and pass as parameter to itself.  
Notice that you do not have to convert ```num``` to string, there is a simpler way: [[reference]](http://stackoverflow.com/questions/478968/sum-of-digits-in-c-sharp)  
```sum = 0;
while (n != 0) {
    sum += n % 10;
    n /= 10;
}```

## #260 Single number III
**LeetCode Link**:  
[https://leetcode.com/problems/single-number-iii/](https://leetcode.com/problems/single-number-iii/)  
**Problem description**:  
Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once. 
For example: Given nums = [1, 2, 1, 3, 2, 5], return [3, 5].  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/260_SingleNumberIII.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/260_SingleNumberIII.cs)  
**Explanation**:  
- Bitwise way (564ms):  
    1. Get the bitwise XOR result of the array.  
    For the numbers in pair, the XOR result will be 0. Thus after doing XOR one by one for the whole array, the result will be the XOR of the 2 single numbers, assume it's called ```aXORb```.
    2. Get the last set bit of the ```aXORb```.  
    Because a and b are distinct, ```aXORb``` will have at least 1 bit is set (is 1). We need to find one of the set bit.  
    Why? Because at this specific bit, one of ```a``` and ```b``` would be 1 (let's say ```a```), and the other must be 0 (let's say ```b```), and use this feature we could group up all the numbers in the array into 2 groups.
    One of this group will all have this bit set to 1 (let's say group ```a```), and the other group will all have this bit set to 0 (let's say group ```b```). The number of numbers in each group does not matter, because we will do XOR for each group, and the ones in pairs will all end up to 0, the only one left of group a will be a, and the only one left of group b will be b.  
    How? ```int lastSetBit = aXORb & (-aXORb)``` can be used to find the last set bit. In C# ```int``` uses 2's complment (I suppose so, correct me if wrong) for negative number. For example, ```3``` would be ```0011``` in binary, and ```-3``` would be ```1101```, that ```0011 XOR 1101``` leads to ```0001```, which is the last set bit.
    3. Group numbers into 2 groups.  
    Iterate through the array, check condition ```(number & lastSetBit) == 0``` to group up, and XOR through each group, you will finally get a and b.

## #268 Missing number
**LeetCode Link**:  
[https://leetcode.com/problems/missing-number/](https://leetcode.com/problems/missing-number/)  
**Problem description**:  
Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.
For example, Given nums = [0, 1, 3] return 2. Requires O(n) time complexity and O(1) space complexity.
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/268_MissingNumber.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/268_MissingNumber.cs)  
**Explanation**:  
- sum solution:  
```nums``` is not sorted, we cannot sort it because the sorting time complexity would be O(nlogn). ```nums``` has at most 1 missing number, thus the basic strategy to solve this question is to fined expected sum and actual sum of ```nums```, and ```expectedSum - actualSum``` will be the missing number we want. However, there are several corner cases we need to consider:```1. missing 0 (should return 0);2. missing nothing (should return max of nums + 1)```  
To cover these corner cases, we calculate the sum: ```sum = nums.Length * (nums.Length + 1) / 2```, and iterate through ```nums``` to do ```sum -= nums[i]```. So if 0 is missing, it returns 0; if number is missing in between, it will return the number; if no number is missing, it will return ```nums.Length```.  

## #283 Move Zeroes
**LeetCode Link**:  
[https://leetcode.com/problems/move-zeroes/](https://leetcode.com/problems/move-zeroes/)  
**Problem description**:  
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements. For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/283_MoveZeroes.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/283_MoveZeroes.cs)  
**Explanation**:  
- Iteration way (492ms), refer to [[fetoyal's solution]](https://leetcode.com/discuss/59355/3-lines-o-1-space-o-n-time-c):  
Iterate through to find none-zero number and move to the front. Thanks to fetoyal's brillient solution.

## #292 Nim Game
**LeetCode Link**:  
[https://leetcode.com/problems/nim-game/](https://leetcode.com/problems/nim-game/)  
**Problem description**:  
You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.

Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.

For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.  
**Source code**:  
[https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/292_NimGame.cs](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/292_NimGame.cs)  
**Explanation**:  
- 1 line solution:  
Counting backwards, for the first 3, you win any way; if you are at 4th, you lose anyway; if 5,6,7, you can put your oppenent to 4 to win the game; if 8, your oppenent will end up 5 or 6 or 7, you lose ... so you see the pattern
