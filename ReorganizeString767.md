# 题目
Given a string S, check if the letters can be rearranged so that two characters that are adjacent to each other are not the same.\
If possible, output any possible result.  If not possible, return the empty\
Note:\
S will consist of lowercase letters and have length in range [1, 500].string.\
重建字符串，使得相邻的字符不相同。
# 样例输出
Example 1:\
Input: S = "aab"\
Output: "aba"\
Example 2:\
Input: S = "aaab"\
Output: ""
# 分析
我的做法是建立一个vector容器，从头遍历字符串，遇到不同的字符则将其push到容器中，然后每次，然后将已经push过的字符设为“ ”，以后不再考虑“ ”的存在，然后再从原先位置开始继续往后遍历，直到不能找到不同的字符为止。
# 程序实现
```cpp
class Solution {
public:
    string reorganizeString(string S) {
       string::iterator p1=S.begin();
       vector<char>h;
        h.push_back(*p1);
        char a=*p1;
        p1++;
         string::iterator p3=p1;
        while(p3!=S.end()){
            p1=p3;
            while(*p1==a)
            p1++; 
            if(*p1=' '){
                h.push_back(*p1);
                a=*p1;
             *p1=' ';
            }
        }
        if(h.size()==S.size())
        {
           char* b=new char[h.size()+1];
            int i=0;
            vector<char>::iterator p2=h.begin();
            while(p2!=h.end()){
                b[i]=*p2;
                i++;p2++;
            }
            return b;
        }
        else
         {  
            string a;
          return a;
         }
        
    }
};
```
