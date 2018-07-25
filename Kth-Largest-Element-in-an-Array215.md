# 题目
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.\
Note:\
You may assume k is always valid, 1 ≤ k ≤ array's length.

# 样例输出
Example 1:

Input: [3,2,1,5,6,4] and k = 2\
Output: 5

Example 2:

Input: [3,2,3,1,2,4,5,5,6] and k = 4\
Output: 4

# 分析
简单粗暴，对nums数组排序，输出第nums.size()-k个数即可
# 程序实现
```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        int kth;
        sort(nums.begin(),nums.end());
            kth=nums[nums.size()-k];
        return kth;
            
    }
};
```