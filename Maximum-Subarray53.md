# 题目
DescriptionHintsSubmissionsDiscussSolution

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.
# 样例输出
Example:

Input: [-2,1,-3,4,-1,2,1,-5,4],\
Output: 6\
Explanation: [4,-1,2,1] has the largest sum = 6.

Follow up:

If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.
# 分析
动态规划，设定一个大小为nums.size()*nums.size()的数组，状态转移方程为[i][j]=[i-1][j-1]+[0][j]，然后选取数组中最大的元素返回即可\
类似的递归也能实现\
但是两种都超时了。。。。。。。。。
# 程序实现
* 动态规划
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n=nums.size();
        int a[n][n]={0};
        int sum=INT_MIN;  
        for(int i=0;i<n;i++)
            a[0][i]=nums[i];
        for(int i=1;i<n;i++){
            for(int j=i;j<n;j++)
            { 
                a[i][j]=a[i-1][j-1]+a[0][j];
            sum=max(sum,a[i][j]);
        }
        }
       
        return sum;
    }
    
};
//状态转移方程[i][j]=[i-1][j-1]+[0][j]
```
* 递归
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n=nums.size();
        int sum=INT_MIN; 
        for(int i=1;i<n;i++){
            for(int j=i;j<n;j++)
            sum=max(sum,found(i,j,nums));
        }
       
        return sum;
    }
     int found(int i,int j,vector<int>& nums){
        if(i=0)
            return nums[j];
       else
           return found(i-1,j-1,nums)+found(0,j,nums);
    }
    
};
//状态转移方程[i][j]=[i-1][j-1]+[0][j]
