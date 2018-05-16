# 题目
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.
# 样例输出
Example 1:

Input: [2,3,1,1,4]\
Output: true\
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.

Example 2:

Input: [3,2,1,0,4]
Output: false\
Explanation: You will always arrive at index 3 no matter what. Its maximum  jump length is 0, which makes it impossible to reach the last index.
# 分析
看到hint里面对这个题的归类是greedy贪心算法，那么就可以对nums进行遍历，用step来记录每一个nums数组元素，然后比较当前位置的i加上step再加上1是否可以等于nums的大小即可。
# 程序实现
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        if(nums.size()==1)
            return true;
     int step=INT_MIN;
        for(int i=0;i<nums.size();i++){
            if(nums[i]>step){
                step=nums[i];
            }
            if((nums.size()-i-1)<=step)
                return true;
            if(step==0)
            return false;
        step--;
        }
        return false;
        
    }
};
```
参考：
[https://blog.csdn.net/qq_32400847/article/details/51336300]