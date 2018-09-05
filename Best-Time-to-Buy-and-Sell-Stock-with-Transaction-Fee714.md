# 题目
Your are given an array of integers prices, for which the i-th element is the price of a given stock on day i; and a non-negative integer fee representing a transaction fee.

You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction. You may not buy more than 1 share of a stock at a time (ie. you must sell the stock share before you buy again.)

Return the maximum profit you can make.\
Note:\
0 < prices.length <= 50000.\
0 < prices[i] < 50000.\
0 <= fee < 50000.
# 样例输出
Example 1:

Input: prices = [1, 3, 2, 8, 4, 9], fee = 2\
Output: 8\
Explanation: The maximum profit can be achieved by:\
Buying at prices[0] = 1\
Selling at prices[3] = 8\
Buying at prices[4] = 4\
Selling at prices[5] = 9\
The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.
# 分析
* 动态规划：\
把每一天拥有的资金划分为两部分：可流动的现金fle和此时的股票值stock,现金fle为返回值，现金fle两种状态：(1)保持不动(2)卖股票赚钱．　股票值stock两种状态：(1)保持不动(2)现有的fle拿去买股票
# 程序实现
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices, int fee) {
        int fle=0;
        int stock=-prices[0];
        for(int i=1;i<prices.size();i++){
            fle=max(fle,prices[i]+stock-fee);//不动的钱＆卖股票赚之后的钱
            stock=max(stock,fle-prices[i]);//不动的股票值＆买股票之后的股票值
        }
        return fle;
    }
};
```