# 题目
Given a string, sort it in decreasing order based on the frequency of characters.
# 样例输出
Example 1:\
Input:\
"tree"\
Output:\
"eert"\
Explanation:\
'e' appears twice while 'r' and 't' both appear once.\
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.

Example 2:\
Input:\
"cccaaa"\
Output:\
"cccaaa"\
Explanation:\
Both 'c' and 'a' appear three times, so "aaaccc" is also a valid answer.\
Note that "cacaca" is incorrect, as the same characters must be together.

Example 3:\
Input:\
"Aabb"\
Output:\
"bbAa"\
Explanation:\
"bbaA" is also a valid answer, but "Aabb" is incorrect.\
Note that 'A' and 'a' are treated as two different characters.
# 分析
用map存放对应字符和次数，然后放入字符串result里即可。
# 程序实现
```cpp
class Solution {
public:
    string frequencySort(string s) {
        sort(s.begin(),s.end());
        multimap<int,char>res;
        char result[s.size()]={'a'};
        for(int i=0;i<s.size();i++){
            int j=i+1;
            while(s[i]==s[j])
                j++;
            int time=j-i;
            res.insert(make_pair<time,s[i]>);
            i=j;
        }
        multimap<int,char>:: iterator p=res.begin();
        while(p!=res.end())
        {
            for(int k=0;k<p->first;k++)
                result[k]=(p->second);
        }
        return result; 
    }
};
```