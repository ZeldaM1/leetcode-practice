# 题目
Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.\
Note:

* You must not modify the array (assume the array is read only).
* You must use only constant, O(1) extra space.
* Your runtime complexity should be less than O(n2).
* There is only one duplicate number in the array, but it could be repeated more than once.


# 样例输出
Example 1:

Input: [1,3,4,2,2]\
Output: 2

Example 2:

Input: [3,1,3,4,2]\
Output: 3
# 分析
就是一个找重复数字的题。\
solution1：\
设定两个for循环遍历数组，找到即可。
solution2：\
将数组排序。相同数字必定连在一起，则for循环找到前后相同的数即可。
# 程序实现
* 368ms
```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        for(int i=0;i<nums.size();i++){
            for(int j=i+1;j<nums.size();j++){
                if(nums[i]==nums[j])
                    return nums[i];
            }
        }
    }
};
```
* 8ms
```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size()-1;i++){
            if(nums[i]==nums[i+1])
               return nums[i];
               }
    }
};