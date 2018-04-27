# 题目
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.\
给定一个整数数组和一个整数k，您需要找到总数等于k的连续子数组的总数。\
Note:\
The length of the array is in range [1, 20,000].\
The range of numbers in the array is [-1000, 1000] and the range of the integer k is [-1e7, 1e7].
# 样例输出
Example 1:\
Input:nums = [1,1,1], k = 2\
Output: 2
# 分析
* 超时做法：本来的想法是从数组第一个元素开始，遍历数组，用sum来累加直到找到等于k的位置，否则再从第二个元素开始寻。
* AC做法：用一个长度为nums.size()+1的容器来存放sum的值，使得容器内元素从0开始，后面每一个sum元素都是对应位置nums元素累加值，然后对sum的每一个值进行遍历，若有等于k的则使得count+1，最后返回count值。
# 程序实现
```cpp
超时：
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        vector<int>::iterator i;
        int count=0;
        for(i=nums.begin();i!=nums.end();i++){
        int sum=0;
        while(sum<k)
        {
            sum+=*i;
            i++;
        }
        if(sum==k)
            count++;
        }
        return count;
    }
};
```
```cpp
AC:
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) { 
          int n = nums.size(), count = 0;  
        vector<int> sum(n+1, 0);  
        for(int i=0; i<n; ++i) 
            sum[i+1] = sum[i] + nums[i];  
        for(int i=0; i<n; ++i) {  
            for(int j=i+1; j<=n; ++j) {  
                if(sum[j] - sum[i] == k)
                    ++count;  
            }  
        }  
        return count;  
    }  
};  