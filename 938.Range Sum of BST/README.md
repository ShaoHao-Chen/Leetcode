# 938. Range Sum of BST

## Binary Tree;Recursion;In order traversal;

Given the `root` node of a binary search tree and two integers `low` and `high`, return *the sum of values of all nodes with a value in the **inclusive** range* `[low, high]`.

### Example 1:

![example1](.\img\example1.jpg)

```
Input: root = [10,5,15,3,7,null,18], low = 7, high = 15
Output: 32
Explanation: Nodes 7, 10, and 15 are in the range [7, 15]. 7 + 10 + 15 = 32.
```

## Solution 1, **Iteration** 

### - Time Complexity: O(n) [n=number of nodes]

### - Space Complexity: O(h) [h=height of tree] [Considering recursive calls]

```c++
class Solution {
public:
    int rangeSumBST(TreeNode* root, int low, int high) {
        int ans=0;
        helper(root, low, high, ans);
        return ans;
    }
private:
    void helper(TreeNode *root, int low, int high, int &ans){
        if(root==nullptr) return;
        if(root->val < low){
            helper(root->right, low, high, ans);
        }
        if(root->val>=low && root->val <= high){
            ans += root->val;
            helper(root->right, low, high, ans);
            helper(root->left, low, high, ans);
        }
		if(root->val > high){
            helper(root->left, low, high, ans);
        }
    }
};
```

