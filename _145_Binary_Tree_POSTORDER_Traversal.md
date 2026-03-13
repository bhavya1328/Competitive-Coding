# Binary Tree POSTORDER Traversal

## Problem Statement:
145. Binary Tree Postorder Traversal
Solved
Easy
Topics
premium lock icon
Companies
Given the root of a binary tree, return the postorder traversal of its nodes' values.

 

Example 1:

Input: root = [1,null,2,3]

Output: [3,2,1]

Explanation:



Example 2:

Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]

Output: [4,6,7,5,2,9,8,3,1]

Explanation:



Example 3:

Input: root = []

Output: []

Example 4:

Input: root = [1]

Output: [1]

 

Constraints:

The number of the nodes in the tree is in the range [0, 100].
-100 <= Node.val <= 100



## approach: 
1️⃣ Approach (Using Recursion – Most Common)
Step-by-Step Logic

Create a result list to store the traversal.

Create a recursive function postorder(TreeNode root).

Base case:

If root == null → return.

Traverse the left subtree

Traverse the right subtree

Add the root value to the result list

Return the result list.

Because in postorder traversal we process the root last.




## code:

```java
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
class Solution {
    List<Integer> ans = new ArrayList<>();
    public List<Integer> postorderTraversal(TreeNode root) {
        helper(root);
        return ans;    
    }

    public void helper(TreeNode root) {
        if(root == null)
            return;

        //LRP
        helper(root.left);
        helper(root.right);
        ans.add(root.val);
    }
}
```