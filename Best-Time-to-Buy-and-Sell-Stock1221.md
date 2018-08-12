# 题目
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

# 样例输出
Example 1:\
Input: [7,1,5,3,6,4]\
Output: 5\
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.\
Not 7-1 = 6, as selling price needs to be larger than buying price.

Example 2:\
Input: [7,6,4,3,1]\
Output: 0\
Explanation: In this case, no transaction is done, i.e. max profit = 0.
# 分析
* solution1:\
简单粗暴，直接两个for循环遍历数组，找到最大的buy和sell差值即可。
* solution2:\
一个for循环来寻找最小的buy和最大的利润\
感觉和动态规划没什么关系。。。
# 程序实现
* solution1
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if(prices.size()==0||prices.size()==1)
            return 0;
        int b=0;
        for(int i=0;i<prices.size()-1;i++){
            for(int j=i+1;j<prices.size();j++){
                b=max(b,prices[j]-prices[i]);
            }
        }
       
        return b;
    }
};
```
* solution2:官方的java，看个思路
```java
public class Solution {
    public int maxProfit(int prices[]) {
        int minprice = Integer.MAX_VALUE;
        int maxprofit = 0;
        for (int i = 0; i < prices.length; i++) {
            if (prices[i] < minprice)
                minprice = prices[i];
            else if (prices[i] - minprice > maxprofit)
                maxprofit = prices[i] - minprice;
        }
        return maxprofit;
    }
}
```
