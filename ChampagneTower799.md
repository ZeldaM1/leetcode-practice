# 题目
We stack glasses in a pyramid, where the first row has 1 glass, the second row has 2 glasses, and so on until the 100th row.  Each glass holds one cup (250ml) of champagne.
Then, some champagne is poured in the first glass at the top.  When the top most glass is full, any excess liquid poured will fall equally to the glass immediately to the left and right of it.  When those glasses become full, any excess champagne will fall equally to the left and right of those glasses, and so on.  (A glass at the bottom row has it's excess champagne fall on the floor.)\
倒香槟问题。
# 样例输出
Example 1:\
Input: poured = 1, query_glass = 1, query_row = 1\
Output: 0.0\
Explanation: We poured 1 cup of champange to the top glass of the tower (which is indexed as (0, 0)). There will be no excess liquid so all the glasses under the top glass will remain empty.

Example 2:\
Input: poured = 2, query_glass = 1, query_row = 1\
Output: 0.5\
Explanation: We poured 2 cups of champange to the top glass of the tower (which is indexed as (0, 0)). There is one cup of excess liquid. The glass indexed as (1, 0) and the glass indexed as (1, 1) will share the excess liquid equally, and each will get half cup of champange.
# 分析
我的做法就是很普通的判断第query_row行的总的装满酒的酒杯个数，然后比较酒杯个数和给的酒的总量之间的关系即可。
# 程序实现
```cpp
 int sum=0,all=0;
   double glass=1;
   double m;
class Solution {
public:
    double champagneTower(int poured, int query_row, int query_glass) {
     for(int i=0;i<=query_row;i++){
            	all+=sum;
				sum=i+1;
			}	
       m=poured-all;
        if(m<=0)
          glass=0;
            else if(m>0)
            {
       	if(query_glass==1||query_glass==sum)
       	{
       		if(sum==2)
       		glass=m/2;
       		else
       		glass=(m/(2*sum));
		   }
		   else
		   glass=(m-(m/sum))/(sum-2);
	}
	return glass;
}
};
```
* 本地运行对的放在leetcode上就是WA就很迷。。。:flushed:  :flushed: