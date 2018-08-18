# 题目
 In LeetCode Store, there are some kinds of items to sell. Each item has a price.

However, there are some special offers, and a special offer consists of one or more different kinds of items with a sale price.

You are given the each item's price, a set of special offers, and the number we need to buy for each item. The job is to output the lowest price you have to pay for exactly certain items as given, where you could make optimal use of the special offers.

Each special offer is represented in the form of an array, the last number represents the price you need to pay for this special offer, other numbers represents how many specific items you could get if you buy this offer.

You could use any of special offers as many times as you want.
# 样例输出
Example 1:

Input: [2,5], [[3,0,5],[1,2,10]], [3,2]\
Output: 14\
Explanation: 

There are two kinds of items, A and B. Their prices are $2 and $5 respectively. \
In special offer 1, you can pay $5 for 3A and 0B\
In special offer 2, you can pay $10 for 1A and 2B. \
You need to buy 3A and 2B, so you may pay $10 for 1A and 2B (special offer #2), and $4 for 2A.

Example 2:

Input: [2,3,4], [[1,1,0,4],[2,2,1,9]], [1,2,1]\
Output: 11\
Explanation: \
The price of A is $2, and $3 for B, $4 for C. \
You may pay $4 for 1A and 1B, and $9 for 2A ,2B and 1C. \
You need to buy 1A ,2B and 1C, so you may pay $4 for 1A and 1B (special offer #1), and $3 for 1B, $4 for 1C. \
You cannot add more items, though only $9 for 2A ,2B and 1C.

Note:

    There are at most 6 kinds of items, 100 special offers.
    For each item, you need to buy at most 6 of them.
    You are not allowed to buy more items than you want, even if that would lower the overall price.
# 分析
卧槽没做出来...现在想出来的只能解决使用单个套餐的情况,而不能结合多个套餐情况.....干!!
# 程序实现
```cpp
class Solution {
public:
    int shoppingOffers(vector<int>& price, vector<vector<int>>& special, vector<int>& needs) {
         vector<vector<int>>&set=special;
        int money=0;
        int a=INT_MAX;
        for(int i=0;i<needs.size();i++)
            money+=price[i]*needs[i];
        
        for(int i=0;i<special.size();i++){
          for(int j=0;j<needs.size();j++){
              if(set[i][j]==0)
                  continue;
              a=min(needs[j]/set[i][j],a);//最小整除数
          }
             set[i][special[0].size()-1]=a* set[i][special[0].size()-1];//最小整除数*套餐价格
             for(int j=0;j<needs.size();j++){
                 set[i][j]=needs[j]-a*set[i][j];
                set[i][special[0].size()-1]+=price[j]*set[i][j];//加上余下的钱
             }
             
           money=min(money,set[i][special[0].size()-1]);
        }
        return money;
    }
};
```