class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        int sum=0;
        for(int i=0;i<nums.size();i++)
            sum+=nums[i];
        if(sum<s||nums.size()==0)
            return 0;
    }
    sum=0; 
    int p1=0,p2=1;
    while(){
        while(sum<s){
            sum+=nums[p2];
            p2++;
        }
        if(sum>s)
        {  sum-=nums[p1];
        p1++;}
    }
};# 题目
Given an array of n positive integers and a positive integer s, find the minimal length of a contiguous subarray of which the sum ≥ s.
If there isn't one, return 0 instead. 
# 样例输出
For example, given the array [2,3,1,2,4,3] and s = 7\
the subarray [4,3] has the minimal length under the problem constraint. 
# 分析
# 程序实现
```cpp
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        int sum=0;
        for(int i=0;i<nums.size();i++)
            sum+=nums[i];
        if(sum<s||nums.size()==0)
            return 0;
    }
};
