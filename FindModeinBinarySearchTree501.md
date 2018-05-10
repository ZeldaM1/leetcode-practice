# 题目
Given a binary search tree (BST) with duplicates, find all the mode(s) (the most frequently occurred element) in the given BST.
Assume a BST is defined as follows: 
The left subtree of a node contains only nodes with keys less than or equal to the node's key.
The right subtree of a node contains only nodes with keys greater than or equal to the node's key.
Both the left and right subtrees must also be binary search trees.\
找出二叉树中出现频率最高的数。
# 样例输出
```
For example:
Given BST [1,null,2,2],
   1
    \
     2
    /
   2

return [2]. 
```
Note: If a tree has more than one mode, you can return them in any order. 
Follow up: Could you do that without using any extra space? (Assume that the implicit stack space incurred due to recursion does not count). 

# 分析
我的方法是对二叉树进行遍历（分别设定left和right来统计左子树和右子树），用map记录下对应的数字和出现次数，然后对map进行遍历，找到次数最多的那个值并将其放入vector里返回即可。
一直runtime就很迷。。。\
然后发现大佬用了map和栈结合的方法。
# 程序实现
* 我的
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
vector<int>f;
    map<int,int>res;
    int key;
    int value;
class Solution {
public:
     void findleft(TreeNode* root){
         while(root){
         int m=root->val;
    	res[m]++;
        findleft(root->left);
         }
    }
    void findright(TreeNode* root){
        while(root){
    	int n=root->val;
    	res[n]++;
        findright(root->right);
	}
    }
    vector<int> findMode(TreeNode* root) {
        findright(root);
        findleft(root);
		 map<int,int>::iterator p=res.begin();
		 key=p->first;
		 value=p->second;
		 p++;
		 while(p!=res.end())
		 {
		 	
		 	if(p->second>value){
		 		value=p->second;
		 		key=p->first;
			 }
			 p++;
		 }
		 f.push_back(key);
        return f;
    }
};
```
* 大佬做法
```
vector<int> res;
        if(!root) return res;
        unordered_map<int, int> mp;
        stack<TreeNode *> s;
        s.push(root);
        while (!s.empty()) {
            root = s.top();
            s.pop();
            ++mp[root->val];
            if (root->right) s.push(root->right);
            if (root->left) s.push(root->left);
        }
        int maxcnt = 0;
        for (auto mmp:mp) {
            maxcnt = max(mmp.second, maxcnt);
        }
        for (auto mmp:mp) {
            if (mmp.second == maxcnt) res.push_back(mmp.first);
        }
        return res;
    }
};
```
[https://segmentfault.com/a/1190000011101356]