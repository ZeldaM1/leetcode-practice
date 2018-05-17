# 题目
Given a set of distinct integers, nums, return all possible subsets (the power set).\
Note: The solution set must not contain duplicate subsets.\
求出数列的子列。
# 样例输出
Example:

Input: nums = [1,2,3]\
Output:\
[\
  [3],\
  [1],\
  [2],\
  [1,2,3],\
  [1,3],\
  [2,3],\
  [1,2],\
  []\
]
# 分析
本来想单纯的用for循环，然后发现for循环只能取得在数列中连续的子列，然后看到大神用了回溯法，从位置0开始往后查找，然后在查找中若寻找到了最后一个位置则返回已取得的数列，否则需要将当前位置的下一个位置放入查找的函数中，如此循环直至遍历完数列。
* 注意：函数中的a，b一定加&，否则只能输出一个元素。
# 程序实现
```cpp
void find(int i,vector<int>& num,vector<vector<int>>&c,vector<int>&d){
    if(i==num.size())
        return;
    for(int j=i;j<num.size();j++){
        d.push_back(num[j]);
        c.push_back(d);
        find(j+1,num,c,d);
         d.pop_back();
    }
}
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>>a;
        vector<int>b;
        a.push_back(b);
        find(0,nums,a,b);
        return a;
    }
};