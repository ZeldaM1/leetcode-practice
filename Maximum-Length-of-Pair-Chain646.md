# 题目
You are given n pairs of numbers. In every pair, the first number is always smaller than the second number.

Now, we define a pair (c, d) can follow another pair (a, b) if and only if b < c. Chain of pairs can be formed in this fashion.

Given a set of pairs, find the length longest chain which can be formed. You needn't use up all the given pairs. You can select pairs in any order.
Note:

    The number of given pairs will be in the range [1, 1000].
# 样例输出
Example 1:

Input: [[1,2], [2,3], [3,4]]\
Output: 2\
Explanation: The longest chain is [1,2] -> [3,4]
# 分析
常规做法：把数组元素按照第一个数的大小从小到大排序，然后遍历数组，统计符合条件的数即可
# 程序实现
```cpp
class Solution {
public:
 
    void Sort(vector<vector<int> >& pairs){
       for(int i =0;i < pairs.size() - 1;i++)
            {
                for(int j = 0;j <  pairs.size()-1-i;j++)
                {
                    if(pairs[j][0] >pairs[j+1][0])
                    {
                        swap(pairs[j],pairs[j+1]);
                    }
                    else if(pairs[j][0]==pairs[j+1][0])
                    {
                        if(pairs[j][1] >pairs[j+1][1])
                    {
                            swap(pairs[j],pairs[j+1]);
                    }
                }
            }
       }
        
    }
    int findLongestChain(vector<vector<int> >& pairs) {
      
        Sort(pairs);
         int all1=1;
        int all;
      
        for(int i=0;i<pairs.size()-1;i++){
            all=1;
            int now=pairs[i][1];
            vector<int>c;
            int j=i+1;
            for(j=i+1;j<pairs.size();j++){
                if(now<pairs[j][0])
                {
                all++;
				now=pairs[j][1];
                		while(j+1<pairs.size()){
                				c.clear();
					c.push_back(pairs[j][0]);
                		c.push_back(pairs[j][1]);
                			if(c==pairs[j+1])
                			{
							all++;
                			j++;}
                			else
                			break;
						}
				}
          
            }
          all1=max(all,all1);
        }
        return all1;
    }  
};
```
