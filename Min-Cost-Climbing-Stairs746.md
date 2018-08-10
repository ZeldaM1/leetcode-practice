# 题目
On a staircase, the i-th step has some non-negative cost cost[i] assigned (0 indexed).
Once you pay the cost, you can either climb one or two steps. You need to find minimum cost to reach the top of the floor, and you can either start from the step with index 0, or the step with index 1.
Note:

    cost will have a length in the range [2, 1000].
    Every cost[i] will be an integer in the range [0, 999].

# 样例输出
Example 1:\
Input: cost = [10, 15, 20]\
Output: 15\
Explanation: Cheapest is start on cost[1], pay that cost and go to the top.

Example 2:\
Input: cost = [1, 100, 1, 1, 1, 100, 1, 1, 100, 1]\
Output: 6\
Explanation: Cheapest is start on cost[0], and only step on 1s, skipping cost[3].
# 分析
由题目可知：\
0th:all[0]=min(0、cost[0])\
1st:all[1]=min(0+cost[1]、cost[0]+cost[1])
2nd:1st跳1、0th跳2 -> all[2]=min(all[0]+cost[2],all[1]+cost[2])\
3rd:1st跳2、2nd跳1 -> all[3]=min(all[1]+cost[3],all[2]+cost[3])
4th:2nd跳2、3rd跳1 ->all[4]=min(all[2]+cost[4],all[3]+cost[4])\
...\
nth:(n-1)th跳1、(n-2)th跳2 -> all[n]=min(all[n-1]+cost[n],all[n-2]+cost[n])
# 程序实现
```cpp
class Solution {
public:
    int minCostClimbingStairs(vector<int>& cost) {
        if(cost.size()==2)
            return cost[0],cost[1];
        int money1=0,money2=0,all;
        for(int i=2;i<=cost.size();i++){
            all=min(money1+cost[i-1],money2+cost[i-2]);
            money2=money1;
            money1=all;
        }
        
        
        return all;
    }
};