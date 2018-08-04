# 题目
A sequence of numbers is called a wiggle sequence if the differences between successive numbers strictly alternate between positive and negative. The first difference (if one exists) may be either positive or negative. A sequence with fewer than two elements is trivially a wiggle sequence.\
For example, [1,7,4,9,2,5] is a wiggle sequence because the differences (6,-3,5,-7,3) are alternately positive and negative. In contrast, [1,4,7,2,5] and [1,7,4,5,5] are not wiggle sequences, the first because its first two differences are positive and the second because its last difference is zero.\
Given a sequence of integers, return the length of the longest subsequence that is a wiggle sequence. A subsequence is obtained by deleting some number of elements (eventually, also zero) from the original sequence, leaving the remaining elements in their original order.\
Follow up:\
Can you do it in O(n) time? 
# 样例输出
Examples:\
Input: [1,7,4,9,2,5]\
Output: 6\
The entire sequence is a wiggle sequence.

Input: [1,17,5,10,13,15,10,5,16,8]\
Output: 7\
There are several subsequences that achieve this length. One is [1,17,10,13,10,16,8].

Input: [1,2,3,4,5,6,7,8,9]\
Output: 2
# 分析
由题可知，当nums大小在2以内是算作wiggle sequence，当nums中有两个相邻的元素时忽略即可。\
将length设定为整个nums的大小，有相邻元素的时候则用length减去相同元素数目即可。
可以设定一个flag来记录两个相邻的元素之间差的符号：\
若符号连续，则length--\
若符号是+-交错则可以将flag依次取1，-1
# 程序实现
```cpp
class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        int length=nums.size();
        int flag = 0;
        if(nums.size()<2)
        {
            return length;
        }
      
        for(int i = 1; i < nums.size(); i++)
        {
            if(nums[i]-nums[i-1] == 0) 
                length--;
            else if(nums[i]-nums[i-1]>0) 
                flag==1?length--:flag=1;
            else if(nums[i]-nums[i-1]<0)
                flag==-1?length--:flag=-1;
        }
        return length;
    }
};
```