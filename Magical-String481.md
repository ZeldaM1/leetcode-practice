# 题目
A magical string S consists of only '1' and '2' and obeys the following rules:

The string S is magical because concatenating the number of contiguous occurrences of characters '1' and '2' generates the string S itself.

The first few elements of string S is the following: S = "1221121221221121122……"

If we group the consecutive '1's and '2's in S, it will be:

1 22 11 2 1 22 1 22 11 2 11 22 ......

and the occurrences of '1's or '2's in each group are:

1 2 2 1 1 2 1 2 2 1 2 2 ......

You can see that the occurrence sequence above is the S itself.

Given an integer N as input, return the number of '1's in the first N number in the magical string S.

Note: N will not exceed 100,000.
# 样例输出
Example 1:\
Input: 6\
Output: 3\
Explanation: The first 6 elements of magical string S is "12211" and it contains three 1's, so return 3.
# 分析
这道题找规律是找不到的。。。只有按照题目给的方法来一步一步构造数组。先构造一个含有122的数组作为基础，然后从第二个2开始往后构造，把获得的数依次加入到数组中直到数组有>=n个数为止，然后count出1的个数即可
# 程序实现
```cpp
class Solution {
public:
    int magicalString(int n) {
        vector<int>a;
        a.push_back(1);
        a.push_back(2);
        a.push_back(2);
        int i=2;
        while(a.size()<n){
        int j=a[i];
        int k=(a[a.size()-1]==1?2:1);
            for(int x=0;x<j;x++)
            {
              a.push_back(k);  
            }
            i++;
        }
        return count(a.begin(),a.begin()+n,1);
    }
};
