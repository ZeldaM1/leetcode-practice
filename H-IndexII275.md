# 题目
Follow up for H-Index: What if the citations array is sorted in ascending order? Could you optimize your algorithm? \
跟进274（H-Index）:如果数组按升序排序，会怎么样?你能优化你的算法吗?
# 分析
在274题中，为了遍历数组方便，对数组进行了排序操作，而这道跟进题中已经明确说数组已排序，故思路可和274相同，省略sort排序这一步即可。
# 程序实现
```cpp
class Solution {
public:
    int hIndex(vector<int>& citations) {
        if(citations.size()==0)
            return 0;  
        int m=citations.size();
        if(citations[citations.size()-1]==0) 
            return 0;  
        int h = 0;  
        for(int i = citations.size()-1; i>=0; i--){  
            if(citations[i]>h) 
                h++;  
        }  
        return h;  
            
    }
};
```
# 总结
开始直接用274的思路然后超时，去掉sort排序即可。
