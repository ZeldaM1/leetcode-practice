# 题目
Given a binary tree, return the tilt of the whole tree.
The tilt of a tree node is defined as the absolute difference between the sum of all left subtree node values and the sum of all right subtree node values. Null node has tilt 0.
The tilt of the whole tree is defined as the sum of all nodes' tilt.\
 给定一个二叉树，返回整个树的倾斜度。\
树节点的倾斜度定义为所有左子树节点值和所有右子树节点值之和的绝对差值。空节点的倾斜度为0。\
整棵树的倾斜度被定义为所有节点倾斜度的总和。\
Note: \
The sum of node values in any subtree won't exceed the range of 32-bit integer.\ 
All the tilt values won't exceed the range of 32-bit integer.
# 样例输出
```
Example:
Input: 
       1
     /   \
    2     3
Output: 1
Explanation: 
Tilt of node 2 : 0
Tilt of node 3 : 0
Tilt of node 1 : |2-3| = 1
Tilt of binary tree : 0 + 0 + 1 = 1
```
# 分析
可以定义一个sum函数来求一个节点的及其子节点的倾斜度，将root作为参数传入sum，然后用递归的方法调用sum函数即可。
# 程序实现
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int all= 0;
    int sum(TreeNode* root){
        if(root == nullptr)
            return 0;
        int left = sum(root->left);
        int right = sum(root->right);
        all += abs(left - right);
        return left + right + root->val;
    }
    int findTilt(TreeNode* root) {
        sum(root);
        return all;
    }
    
};