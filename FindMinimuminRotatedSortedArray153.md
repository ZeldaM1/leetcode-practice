# 题目
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e.,  [0,1,2,4,5,6,7] might become  [4,5,6,7,0,1,2]).

Find the minimum element.

You may assume no duplicate exists in the array.\
找到可以翻转的最小翻转点。
# 样例输出
Example 1:\
Input: [3,4,5,1,2] \
Output: 1

Example 2:\
Input: [4,5,6,7,0,1,2]\
Output: 0
# 分析
由于给出元素已经排好序，故可以采用二分法来查找元素，逐步缩小查找范围，直至找到可翻转点。
# 程序实现
```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int a = 0, b = nums.size()-1, c = 0;
        while (a <b) {
            c = a + (b-a) / 2;
            if (nums[c] > nums[b])
               a = c + 1; 
            else 
                b = c;
        }
        return nums[a];
    }
};