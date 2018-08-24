
# 题目
Given a non-negative integer n, count all numbers with unique digits, x, where 0 ≤ x < 10n.
# 样例输出
Example:

Input: 2\
Output: 91\
Explanation: The answer should be the total numbers in the range of 0 ≤ x < 100, 
             excluding 11,22,33,44,55,66,77,88,99
# 分析
动态规划，用a[i]来保存位数为在i-1，i之间的独立数字的数目，ｂ[ｉ]来保存i位数字的总的数量，状态转移方程：\
a[i]=a[i-1]*(11-i)\
b[i]=b[i-1]+a[i]\
最后返回ｂ的最后一个值即可.
# 程序实现
```cpp
class Solution {
public:
    int countNumbersWithUniqueDigits(int n) {
        if(n==0)
            return 1;
        else if(n==1)
            return 10;
        else if(n==2)
            return 91;
        else{
        vector<int>a(n+1,0);
             vector<int>b(n+1,0);
        a[1]=10;a[2]=81;
            b[1]=10;b[2]=91;
        for(int i=3;i<=n;i++){
               a[i]=a[i-1]*(11-i);
            b[i]=b[i-1]+a[i];
        }
            return b[n];
        }
    }
};