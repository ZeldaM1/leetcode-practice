# 题目
You have a total of n coins that you want to form in a staircase shape, where every k-th row must have exactly k coins.

Given n, find the total number of full staircase rows that can be formed.

n is a non-negative integer and fits within the range of a 32-bit signed integer.
# 样例输出
Example 1:\
n = 5\
The coins can form the following rows:\
¤\
¤ ¤\
¤ ¤\
Because the 3rd row is incomplete, we return 2.\
Example 2:\
n = 8\
The coins can form the following rows:\
¤\
¤ ¤\
¤ ¤ ¤\
¤ ¤\
Because the 4th row is incomplete, we return 3.
# 分析
将n依次减去1,2,3。。。直到不能再减为止，然后比较当前剩余和当前阶梯编号即可。
# 程序实现
```cpp
class Solution {
public:
    int arrangeCoins(int n) {
        if(n==0)
            return 0;
        int left=n;
        int stair=1,stairnum=1;
        while(left>stair){
            left-=stair;
            stair++;
            stairnum++;
        }
        if(left==stairnum)
            return stairnum;
        else
            return (stairnum-1);
    }
};
```