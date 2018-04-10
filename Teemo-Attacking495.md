# 题目
In LOL world, there is a hero called Teemo and his attacking can make his enemy Ashe be in poisoned condition.
Now, given the Teemo's attacking ascending time series towards Ashe and the poisoning time duration per Teemo's attacking, 
you need to output the total time that Ashe is in poisoned condition. 
You may assume that Teemo attacks at the very beginning of a specific time point, and makes Ashe be in poisoned condition immediately.
# 样例输出
Example 1:\
Input: [1,4], 2\
Output: 4\
Explanation: At time point 1, Teemo starts attacking Ashe and makes Ashe be poisoned immediately. \
This poisoned status will last 2 seconds until the end of time point 2. \
And at time point 4, Teemo attacks Ashe again, and causes Ashe to be in poisoned status for another 2 seconds. \
So you finally need to output 4.

Example 2:\
Input: [1,2], 2\
Output: 3\
Explanation: At time point 1, Teemo starts attacking Ashe and makes Ashe be poisoned. \
This poisoned status will last 2 seconds until the end of time point 2. \
However, at the beginning of time point 2, Teemo attacks Ashe again who is already in poisoned status. \
Since the poisoned status won't add up together, though the second poisoning attack will still work at time point 2, it will stop at the end of time point 3.\ 
So you finally need to output 3.
# 分析
题目实际上和mergeintervals一样，就是寻找数轴上重叠的部分，并计算出数轴上重叠部分的长度即可。可以设定一个开始start和一个结束end，
分别代表数轴上的开始和结束的数字，先把start设为从0开始，遍历数组，end的值等于开始时间加上中毒时间duration的值所代表的的点，
然后比较end-start和duration的大小并使得all为all+取得小的那个数，直到遍历完数组，all即为最终中毒时间。
# 程序实现
```cpp
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int all=0;
        int start=0;
        int end;
        for(int i=0;i<timeSeries.size();i++){
            end=timeSeries[i]+duration;
            all += min(duration, end  - start);
                start=end;
        }
        return all;
    }
};
```
# 总结
本来想的是通过比较end和timeSeries[i]后面的数的大小来判断all的取值，然后麻烦的要死，
发现只要判断出中毒时间和end-start两个的大小并取小的那一个和all相加即可。
