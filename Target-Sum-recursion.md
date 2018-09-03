# 题目
 You are given a list of non-negative integers, a1, a2, ..., an, and a target, S. Now you have 2 symbols + and -. For each integer, you should choose one from + and - as its new symbol.

Find out how many ways to assign symbols to make sum of integers equal to target S.\
Note:

    The length of the given array is positive and will not exceed 20.
    The sum of elements in the given array will not exceed 1000.
    Your output answer is guaranteed to be fitted in a 32-bit integer.
# 样例输出
Example 1:

Input: nums is [1, 1, 1, 1, 1], S is 3.\
Output: 5\
Explanation: 

-1+1+1+1+1 = 3\
+1-1+1+1+1 = 3\
+1+1-1+1+1 = 3\
+1+1+1-1+1 = 3\
+1+1+1+1-1 = 3

There are 5 ways to assign symbols to make the sum of nums be target 3.
# 分析
递归：\
全局变量all（初始化为０）：记录有多少种求和方式

sum(初始化为０):记录到当前位置积累的和

从数组的初始位置０处开始向后遍历数组:

(1)若当前位置已到达数组的末尾，则判断sum是否等于target值，若等于则all++,然后跳出函数框
(2)若当前位置未到达数组的末尾，则继续两个递归函数，相应的sum值为+,-之后的值，当前位置移动到下一个位置
# 程序实现
* 递归：
```cpp
class Solution {
public: 
    int all=0;
    int findTargetSumWays(vector<int>& nums, int S) {
      find(0,0,nums,S);
        return all;
        }
    void find(int sum,int j,vector<int>& nums, int S){
        if(j==nums.size()){
            
        if(sum==S)
            all++;
            return ;
        }
        find(sum+nums[j],j+1,nums,S);
        find(sum-nums[j],j+1,nums,S);
    }
};
```