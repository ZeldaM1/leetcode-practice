# 题目
Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n. \
For example, given n = 12, return 3 because 12 = 4 + 4 + 4; given n = 13, return 2 because 13 = 4 + 9. \
给定一个正整数n，找出最少数量的和为n的平方数的组合。
# 样例输出
For example, given n = 12, return 3 because 12 = 4 + 4 + 4; \
given n = 13, return 2 because 13 = 4 + 9. 
# 分析
三种想法：1. 设定一个i使得i<=根号下n的值，然后从i值开始向前推，直到n值为0或i为1（然后这样不能考虑到从0到i中的某个数能被n整除的情况）
2. 设定两个比较函数，一个继承方法1的思想，另一个用来寻找当从0到i中的某个数能被n整除时的i值（然后这种不能考虑到有1，2两种交互的情况）
3. 找规律可知：如果n能够写成a+b*b的情况时，此时的组合数量最小，则可以设定一个长度为n+1的数组，并将每个数都设为最大，
然后将是平方数的对应位置数设为1，再设定两个for循环遍历数组使得寻找到合适的a和b的组合即可。
# 程序实现
```cpp
class Solution {
public:
    int numSquares(int n) {
        vector<int> nums(n + 1, INT_MAX);
        int all;
        for (int i = 0; i*i <= n; ++i)
        {
            nums[i*i] = 1;
        }
        for (int a = 0; a <= n; ++a)
        {
            for (int b = 0; a + b*b <= n; ++b)
            {
                nums[a + b*b] = min(nums[a] + 1, nums[a + b*b]);
            }
        }
        all=nums[n];
        return all;
    }
};
