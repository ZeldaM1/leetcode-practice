# 题目
There are N gas stations along a circular route, where the amount of gas at station i is gas[i]. 
You have a car with an unlimited gas tank and it costs cost[i] of gas to travel from station i to its next station (i+1).
You begin the journey with an empty tank at one of the gas stations. 
Return the starting gas station's index if you can travel around the circuit once, otherwise return -1. 
Note:
The solution is guaranteed to be unique. 
在一个环形路线中有N个加油站，加油站存有的汽油为gas[i],你有一辆车，有一个容量不受限制的汽油箱，从一个车站到另一个车站(i+1)，要耗费cost[i]的汽油。
你开始旅程的时候在其中一个加油站，汽油箱里没有汽油。如果你可以绕着环形一圈的话，返回开始加油站的指针，否则返回-1
# 分析
把下一个加油站的所有油都提前搬到某一个加油站来，并把没油的加油站去掉。
在剩下的加油站中继续寻找油量足以到达下个加油站的站，不断合并加油站，直到只剩一个加油站为止。
那么此时剩余的这个站就能跑完全程。
# 代码
```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
    int n= gas.size()-1;
       int m = 0;
       int all = gas[n] - cost[n];
       while (n > m)
       {
          if (all>= 0)
          {
             all += gas[m] - cost[m];
             ++m;
          }
          else
          {
             --n;
             all+= gas[n] - cost[n];
          }
       }
       return all>= 0 ? n : -1;

    }
};
