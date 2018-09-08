# 题目
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.
# 样例输出
Example 1:

Input: [1,3,5,6], 5\
Output: 2\
Example 2:

Input: [1,3,5,6], 2\
Output: 1\
Example 3:

Input: [1,3,5,6], 7\
Output: 4\
Example 4:

Input: [1,3,5,6], 0\
Output: 0
# 分析
由于数组是有序的，故直接遍历数组找到大于等于target的那个节点即可。
# 程序实现
```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int i=0;
        if(nums[0]==target)
            return 0;
        while(nums[i]<target&&i<nums.size()){
             i++;
        }
        return i;
    }
};
```