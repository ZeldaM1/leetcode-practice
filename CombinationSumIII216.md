# 题目
Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.\
Note:\
All numbers will be positive integers.
The solution set must not contain duplicate combinations.
# 样例输出
Example 1:

Input: k = 3, n = 7\
Output: [[1,2,4]]\
Example 2:

Input: k = 3, n = 9\
Output: [[1,2,6], [1,3,5], [2,3,4]]
# 分析
* 常规思路: 和之前的一样，还是回溯，只需要在判断输出结果时判断一下当前数组大小是否等于k即可。
但是这样回溯效率太低了，跟答案给出的方法一比简直傻爆了。
* 2ms：设定一个长度为k的数组temp并初始化为0，来模拟存放k个数的数组，从i=0的位置开始对数组进行赋值操作，一旦有符合条件的数组temp则将该数组记录下来，如此循环直到1-9的数全部组合完毕。
# 程序实现
* 4ms
```cpp
void com(vector<int>&candidates,vector<vector<int>>&a,vector<int>b,int k,int n,int m){
    if(n==0&&b.size()==k)
    {
         a.push_back(b);
        return ;
    }
      for(int i=m;i<candidates.size();i++){
              b.push_back(candidates[i]);
              com(candidates,a,b,k,n-candidates[i],i+1);
                  b.pop_back();
          }
    }
class Solution {
public:
    vector<vector<int>> combinationSum3(int k, int n) {
         vector<vector<int>>a;
        vector<int>b;
        vector<int>candidates;
        for(int i=1;i<=9;i++)
            candidates.push_back(i);
        com(candidates,a,b,k,n,0);
        return a;
    }
};
```
* 答案2ms
```cpp
class Solution {
public:
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<vector<int>> result;
        vector<int> temp(k, 0);
        int depth = 0;
        int sum = 0;
        while (depth >= 0) {
            if (depth == k) {
                if (sum == n) {
                    result.push_back(temp);
                }
                depth--;
                continue;
            }
            
            if (depth > 0 && temp[depth] == 0) {
                temp[depth] = temp[depth - 1] + 1;
                sum += temp[depth];
            } else {
                temp[depth]++;
                sum++;
            }
            
            if (temp[depth] == 10) {
                sum -= temp[depth];
                temp[depth] = 0;
                depth--;
                continue;
            }
            
            depth++;
        }
        
        return result;
    }
};