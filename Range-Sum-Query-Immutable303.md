# 题目
Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.\\
Note:

    You may assume that the array does not change.
    There are many calls to sumRange function.
# 样例输出
Example:

Given nums = [-2, 0, 3, -5, 2, -1]\\

sumRange(0, 2) -> 1\\
sumRange(2, 5) -> -1\\
sumRange(0, 5) -> -3
# 分析
* solution1:
直接在循环里面把对应位置的数相加
* solution2:
动态规划，状态转移方程为sum[i+1]＝sum[i]+nums[i];
# 程序实现
* solution1:
```cpp
class NumArray {
public:
int * sum=NULL; 
    NumArray(vector<int> nums) {
        sum = new int[nums.size() + 1];
    for (int i = 0; i < nums.size(); i++) {
        sum[i + 1] = sum[i] + nums[i];
    }
    }
    int sumRange(int i, int j) {
       return sum[j+1]-sum[i];
    }
};
/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * int param_1 = obj.sumRange(i,j);
 */
 ```
 * solution2:
 ```cpp
 class NumArray {
public:
    vector<int> num;
    NumArray(vector<int> nums) {
         num=nums;
    }
    
    int sumRange(int i, int j) {
        int sum=0;
        for(int k=i;k<=j;k++){
            sum+=num[k];
        }
        return sum;
    }
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * int param_1 = obj.sumRange(i,j);
 */

