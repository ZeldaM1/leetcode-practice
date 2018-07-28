# 题目
Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.\
Note:

*  The order of the result is not important. So in the above example, [5, 3] is also correct.
* Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?
# 样例输出

Example:

Input:  [1,2,1,3,2,5]\
Output: [3,5]

# 分析
solution1:\
对数组进行排序，第一个开始向后遍历数组，记录下当前数字出现次数直到遍历到的数字不等于当前数字为止(设重复次数为k)，考虑重复次数，若等于1则存入b中，然后使当前指针向后移动k个位置，如此循环下去。
solution2：\
对数组进行排序，则出现一次的数字必定大于其左端数字，小于其右端数字，两头单独讨论
# 程序实现
* 12ms:
```cpp
class Solution {
public:
    vector<int> singleNumber(vector<int>& nums) {
         vector<int>b;
        int k,j;
        if(nums.size()==2&&nums[0]!=nums[1])
            return nums;
         sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size();i+=k){
            j=i+1;
            k=1;
            while(nums[j]==nums[i])
            {
                k++;
                j++;
            }
            if(k==1)
                b.push_back(nums[i]);
    }
        return b;
    }
};
```
* 8ms:
```cpp
class Solution {
public:
    vector<int> singleNumber(vector<int>& nums){
         vector<int>b;
        int i=0;
        sort(nums.begin(),nums.end());
        if(nums[i]!=nums[i+1])
            b.push_back(nums[i]);
         
        for(i=1;i<nums.size()-1;i++){
           if(nums[i]<nums[i+1]&&nums[i]>nums[i-1]){
               b.push_back(nums[i]);
        }
        }
        if(nums[i]!=nums[i-1])
            b.push_back(nums[i]);
        return b;
    }
};