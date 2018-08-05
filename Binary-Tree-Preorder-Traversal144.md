# 题目
Given a binary tree, return the preorder traversal of its nodes' values.\
Follow up:\
Recursive solution is trivial, could you do it iteratively?
# 样例输出
Example:\
Input: [1,null,2,3]\
   1\
    \ \
     2\
    /\
   3\
Output: [1,2,3]
# 分析
递归遍历二叉树即可。
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
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> a;
        recursive(root,a);
            return a;
    }
   void recursive(TreeNode* root,vector<int> & b)
   {
       if(root==NULL)
           return ;
       if(root)
       {
           b.push_back(root->val);
           recursive(root->left,b);
           recursive(root->right,b);
       }
   }
};
```