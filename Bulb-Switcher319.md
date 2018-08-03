# 题目
 There are n bulbs that are initially off. \
 You first turn on all the bulbs
 Then, you turn off every second bulb.\
  On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on).\
   For the i-th round, you toggle every i bulb. \
   For the n-th round, you only toggle the last bulb. Find how many bulbs are on after n rounds.
# 样例输出
Example:

Input: 3\
Output: 1 \
Explanation: \
At first, the three bulbs are [off, off, off].\
After first round, the three bulbs are [on, on, on].\
After second round, the three bulbs are [on, off, on].\
After third round, the three bulbs are [on, off, off]. 

So you should return 1, because there is only one bulb is on.
# 分析
建立数组nums，其中1表示on，0表示off，直接把数组的n个元素全设为1，根据每一次移动的步长和移动次数来改变对应位置的值即可
# 程序实现
```cpp
class Solution {
public:
    int bulbSwitch(int n) {
         int all=0;
        if(n==1)
        all=1;
        else if(n==0)
            all=0;
        else if(n!=1)
        {
            int nums[n]={1};
        int step,now;
        for(int i=1;i<n;i++)
        {
           step=i+1;
            now=i;
            while(now<n){
            if(nums[now]==0)
                nums[now]=1;
            else if(nums[now]==1)
                nums[now]=0;
            now+=step;
            }
        }
       
        for(int i=0;i<n;i++)
            all+=nums[i];
        }
        return all;
    }
};
```
