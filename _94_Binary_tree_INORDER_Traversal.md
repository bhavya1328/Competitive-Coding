# Binary Tree Inorder Traversal

## Problem Statement:
Given the root of a binary tree, return the inorder traversal of its nodes' values.

 

Example 1:

Input: root = [1,null,2,3]

Output: [1,3,2]

Explanation:



Example 2:

Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]

Output: [4,2,6,5,7,1,3,9,8]

Explanation:



Example 3:

Input: root = []

Output: []

Example 4:

Input: root = [1]

Output: [1]

 

Constraints:

The number of nodes in the tree is in the range [0, 100].
-100 <= Node.val <= 100
 

## approach: 
1️⃣ Understand the Traversal Order

For every node in the tree:

Traverse the left subtree

Visit the current node

Traverse the right subtree

Example:

    1
     \
      2
     /
    3

Inorder result → [1, 3, 2]

2️⃣ Approach 1: Recursive (Most Common)
Steps

Create a list to store traversal result.

Define a recursive function inorder(node).

If node is null, return.

Call inorder(node.left) to traverse left subtree.

Add node.val to result list.

Call inorder(node.right) to traverse right subtree.

Return the result list.

Time Complexity

O(n) – every node visited once

Space Complexity

O(n) (recursion stack + result list)

3️⃣ Approach 2: Iterative (Using Stack)

This is often asked in interviews.

Steps

Create:

an empty stack

an empty result list

pointer current = root

Loop while:

current != null OR stack not empty

Traverse left side of tree

push nodes into stack

move current = current.left

When left becomes null:

pop node from stack

add its value to result

Move to right subtree

current = node.right

Repeat until stack empty and current null.

4️⃣ Dry Run Example

Tree:

    1
     \
      2
     /
    3

Process:

Step	Stack	Result
push 1	[1]	[]
pop 1	[]	[1]
push 2	[2]	[1]
push 3	[2,3]	[1]
pop 3	[2]	[1,3]
pop 2	[]	[1,3,2]

Final → [1,3,2]



## code:
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
```java
class Solution {
    List<Integer> ans = new ArrayList<>();
    public List<Integer> inorderTraversal(TreeNode root) {
        helper(root);
        return ans;
    }

    public void helper(TreeNode root) {
        if(root == null)
            return;

        //LPR
        helper(root.left); //L
        ans.add(root.val); //P
        helper(root.right);//R
    }
}
```