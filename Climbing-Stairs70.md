# 题目
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Note: Given n will be a positive integer.
# 样例输出
Example 1:\
Input: 2\
Output: 2\
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps

Example 2:\
Input: 3\
Output: 3\
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
# 分析
由题目可知：\
0th:0\
1st:1
2nd:1st跳1、0th跳2 -> 2\
3rd:1st跳2、2nd跳1 -> 1+2=3\
4th:2nd跳2、3rd跳1 ->2+3=5\
...\
nth:(n-1)th跳1、(n-2)th跳2 -> (n-1)的解+(n-1)的解
# 程序实现
```cpp
class Solution {
public:
    int climbStairs(int n) {
        if(n==1||n==2||n==0)
            return n;
         int a[n+1]={0};
        a[1]=1;
        a[2]=2;
        //a[i]=a[i-1]+a[i-2]
        for(int i=3;i<=n;i++)
        {
            a[i]=a[i-1]+a[i-2];
        }
        return a[n];
    }
};