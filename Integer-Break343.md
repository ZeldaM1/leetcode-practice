# 题目
Given a positive integer n, break it into the sum of at least two positive integers and maximize the product of those integers. Return the maximum product you can get.
Note: You may assume that n is not less than 2 and not larger than 58.\
# 样例输出
Example 1:

Input: 2\
Output: 1\
Explanation: 2 = 1 + 1, 1 × 1 = 1.\
Example 2:

Input: 10\
Output: 36\
Explanation: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36.
# 分析
动态规划
# 程序实现
```cpp
class Solution {
public:
    int integerBreak(int n) {
           vector<int> res(n + 1,1);
        res[3]=2;
        for(int i = 4;i <= n;i++)
        {
            for(int j = 1;j <= i/2;j++)
            {
                res[i] = max(res[i],max(j * res[i - j],j * (i - j)));
            }
        }
        return res[n];
    }
};
```
