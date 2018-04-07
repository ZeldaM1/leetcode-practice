# 题目
Given a sorted array consisting of only integers where every element appears twice except for one element which appears once. 
Find this single element that appears only once. \
给定一个已排序的数组，其中每个元素出现两次，只有一个元素出现一次。查找仅出现一次的单个元素。
# 样例输出
Example 1:
Input: [1,1,2,3,3,4,4,8,8]
Output: 2

Example 2:
Input: [3,3,7,7,10,11,11]
Output: 10

Note: Your solution should run in O(log n) time and O(1) space. 
# 分析
这道题简直简单到爆，直接考虑特殊情况和普遍算法。特殊情况就是排序的数组的第一个数字即为寻找元素，另外就是在数组中寻找这样一个元素：该元素与其前后两个元素的值都不相同。
简直不知道踩了什么呢狗屎运捡到这么一道没有心机的题[笑~]
# 程序实现
```cpp
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        if(nums[0]!=nums[1])
            return nums[0];
        for(int i=1;i<nums.size();i++){
            if(nums[i]!=nums[i-1]&&nums[i]!=nums[i+1])
                return nums[i];
        }
    }
};
```
