# 题目
Given a sorted (in ascending order) integer array nums of n elements and a target value, write a function to search target in nums. If target exists, then return its index, otherwise return -1.

# 样例输出
Example 1:\
Input: nums = [-1,0,3,5,9,12], target = 9\
Output: 4\
Explanation: 9 exists in nums and its index is 4

Example 2:\
Input: nums = [-1,0,3,5,9,12], target = 2\
Output: -1\
Explanation: 2 does not exist in nums so return -1
# 分析
* solution1:直接遍历数组
* solution2:由于数组有小到大排序是确定的，故可采用二分法查找
# 程序实现
* solution1:
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int i;
        for(i=0;i<nums.size();i++){
            if(nums[i]==target)
                return i;
            
        }
        if(i==nums.size())
            return -1;
    }
};
```
* solution2:
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left=0,right=nums.size()-1;
        if(nums.size()==1&&target==nums[0])
            return 0;
        while(left<=right){
            float mid=(left+right)/2;
            if(nums[mid]==target)
                return mid;
            else if(nums[mid]<target)
                left=mid+1;
            else if(nums[mid]>target)
                right=mid-1;
        }
        return -1;
    }
};
```