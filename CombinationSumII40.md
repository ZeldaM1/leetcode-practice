# 题目
Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.
Each number in candidates may only be used once in the combination.\
Note:\
All numbers (including target) will be positive integers.\
The solution set must not contain duplicate combinations.\
给出数组candidates中和为target的组合，每个数字只能用一次。
# 样例输出
Example 1:

Input: candidates = [10,1,2,7,6,1,5], target = 8,\
A solution set is:\
[\
  [1, 7],\
  [1, 2, 5],\
  [2, 6],\
  [1, 1, 6]\
]\
Example 2:

Input: candidates = [2,5,2,1,2], target = 5,
A solution set is:\
[\
  [1,2,2],\
  [5]\
]
# 分析
做法和39.combination_sum相同采取回溯法，但需要注意数组中的每个数字只能用一次，故在回溯时应从当前位置的下一个位置（i+1）处开始。
# 程序实现
```cpp
void com(vector<int>&candidates,vector<vector<int>>&a,vector<int>b,int target,int n){
    if(target==0)
    {
         a.push_back(b);
        return ;
    }
      for(int i=n;i<candidates.size()&&target>=candidates[i];i++){
          if(candidates[i]==candidates[i-1]&&i>n)
              continue;
              b.push_back(candidates[i]);
              com(candidates,a,b,target-candidates[i],i+1);
                  b.pop_back();
          }
    }
class Solution {
public:
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(),candidates.end());
        vector<vector<int>>a;
        vector<int>b;
      com(candidates,a,b,target,0);
        return a;
    }
};