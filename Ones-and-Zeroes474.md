# 题目
In the computer world, use restricted resource you have to generate maximum benefit is what we always want to pursue.

For now, suppose you are a dominator of m 0s and n 1s respectively. On the other hand, there is an array with strings consisting of only 0s and 1s.

Now your task is to find the maximum number of strings that you can form with given m 0s and n 1s. Each 0 and 1 can be used at most once.

Note:

    The given numbers of 0s and 1s will both not exceed 100
    The size of given string array won't exceed 600.
# 样例输出
Example 1:

Input: Array = {"10", "0001", "111001", "1", "0"}, m = 5, n = 3
Output: 4

Explanation: This are totally 4 strings can be formed by the using of 5 0s and 3 1s, which are “10,”0001”,”1”,”0”

Example 2:

Input: Array = {"10", "0", "1"}, m = 1, n = 1
Output: 2

Explanation: You could form "10", but then you'd have nothing left. Better form "0" and "1".
# 分析
solution1：\
遍历整个数字，将每个元素放在寻找0,1数目的函数中，用m减去0的数目，n减去1的数目，只要m，n大于等于0即可进入下一步。但是这样只能保证当前存在的组合数目最多，不一定能保证0,1的组合是最佳的
solution2:\
动态规划问题
# 程序实现
* solution1:(error:)
```cpp
class Solution {
public:
    int zero,one;
    int findMaxForm(vector<string>& strs, int m, int n) {
        sort(strs.begin(),strs.end(),compare);
        int a=0;
        int i=0;
        while(i<strs.size()&&m>=0&&n>=0){
            zero=0;one=0;
            find(strs[i]);
            if((m-zero)>=0&&(n-one)>=0)
            {
                m-=zero;
               n-=one;
            a++;
            }
            i++;
        }
        return a;
        
    }
    bool compare(string c,string b){
        return (c.size()<b.size());
    }
    void find(string x)
    {
        for(int j=0;j<x.size();j++){
            if(x[j]=='1')
                one++;
            else if(x[j]=='0')
                zero++;
        }
    }
};
```
* solution2(动态规划)：
```cpp
class Solution {
public:
    int findMaxForm(vector<string>& strs, int m, int n) {
        int size = strs.size();
        vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));//二维数组代替三维，节省空间

        for (int i = 0; i < size; i++) {
            //计算每个字符串消耗的0和1
            int n0 = 0, n1 = 0;
            for (int j = 0; j < strs[i].length(); j++) if (strs[i][j] == '0') n0++;
            n1 = strs[i].length() - n0;

            //从大往小计算，避免右边找不到其所依赖的上一轮左边的值,若从左到右会过早覆盖旧值
            for (int zero = m; zero >= n0; zero--) {
                for (int one = n; one >= n1; one--) {
                    dp[zero][one] = max(dp[zero][one], 1 + dp[zero - n0][one - n1]);
                }
            }
        }

        return dp[m][n];
    }
};
```