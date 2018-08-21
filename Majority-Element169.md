# 题目
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.
# 样例输出
Example 1:

Input: [3,2,3]\
Output: 3\
Example 2:

Input: [2,2,1,1,1,2,2]\
Output: 2
# 分析
由于题目中的majority element只有一个，故可以遍历数组，记录下出现次数最多的那个数，然后看其出现次数是否大于n/2即可。
# 程序实现
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
      sort(nums.begin(),nums.end());
       
        int i,prev=nums[0],time=1,n=nums.size();
        for(i=1;i<n;i++){
           if(nums[i]==prev)
               time++;
            else if(nums[i]!=prev)
            {
                if(time>n/2)
                    return prev;
                else{
                
                prev=nums[i];
                time=1;
                }
            }
        }
         if(time>n/2)
                    return prev;
    }
};
```
