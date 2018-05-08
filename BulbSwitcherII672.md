# 题目
There is a room with n lights which are turned on initially and 4 buttons on the wall. After performing exactly m unknown operations towards buttons, you need to return how many different kinds of status of the n lights could be. 
Suppose n lights are labeled as number [1, 2, 3 ..., n], function of these 4 buttons are given below: \
Flip all the lights.\
Flip lights with even numbers.\
Flip lights with odd numbers.\
Flip lights with (3k + 1) numbers, k = 0, 1, 2, ...\
有n个灯泡，现在给出m次操作，每次操作都可能是上述四种操作中的一种，求出m次操作之后灯泡情况组合的数量。
# 样例输出
Example 1:\
Input: n = 1, m = 1.\
Output: 2\
Explanation: Status can be: [on], [off]

Example 2:\
Input: n = 2, m = 1.\
Output: 3\
Explanation: Status can be: [on, off], [off, on], [off, off]

Example 3:\
Input: n = 3, m = 1.\
Output: 4\
Explanation: Status can be: [off, on, off], [on, off, on], [off, off, off], [off, on, on].
# 分析
 * 最简单的就是列出每次的情况然后对每次情况进行随机选择然后统计不同情况出现的次数，但是随机组合是不满足程序运行顺序的，此种作废。。
 * 然后就是找规律：
    * n=1              2
    * m=0              1
    * n==2 and m==1    3
    * n==2 or m==1     4
    * m=2              7
    *  m>=3             8\
其余均为8种

# 程序实现
```cpp
        class Solution {
public:
    int flipLights(int n, int m) {
         if(m==0) 
             return 1;
        if(n==1) 
            return 2;
        if(n==2&&m==1)
            return 3;
        if(n==2||m==1) 
            return 4;
        if(m==2) 
            return 7;
        if(m>=3) 
            return 8;
        return 8;
    }
};
