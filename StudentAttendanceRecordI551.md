# 题目
You are given a string representing an attendance record for a student. The record only contains the following three characters: \
\
'A' : Absent. \
'L' : Late.\
'P' : Present. \
\
A student could be rewarded if his attendance record doesn't contain more than one 'A' (absent) or more than two continuous 'L' (late). \
You need to return whether the student could be rewarded according to his attendance record.\
统计学生的出勤次数，若缺勤不超过一次并且迟到不超过连续的两次则可以得到奖励。
# 样例输出
Example 1:\
Input: "PPALLP"\
Output: True\
\
Example 2:\
Input: "PPALLL"\
Output: False
# 分析
本来的想法就是遍历string，然后统计A的次数，如果找到L，则往后推两个遍历，若均为L，则返回false，整个遍历完后，若A次数<=1则返回true，否则返回false.然后超时了。。然后直接对字符串进行遍历，在循环内若发现连续的LLL或者A的次数大于1，则返回false，入欧循环能结束则返回true。（果然原始的最好用）
# 程序实现
```cpp
class Solution {
public:
    bool checkRecord(string s) {
        int a=0,l=0;
     for (int i = 0 ; i < s.size() ; ++i) {  
        if (s[i] == 'A') {  
           a++;  
           l = 0;  
        }
         else if (s[i] == 'L') 
           l++;  
         else
             l=0;
        if (a> 1 || l > 2)
            return false;  
    }  
    return true;  
}
};
```
* 超时的
```
class Solution {
public:
    bool checkRecord(string s) {
        if(s.size()<=3)
            return true;
        else{
        string::iterator p,p2,p3;
        int a=0,l=0;
        for(p=s.begin();p!=s.end();p++)
        {
            if(*p=='A')
                a++;
            else if(*p=='L')
            {
                p2=++p;
                p3=++p2;
                if(p2!=s.end()&&p3!=s.end())
                {
                if(*p2=='L'&&*p3=='L')
                   return false;
                }
            }
        }
        if(a<=1)
            return true;
        else
            return false;
    }
    }
};
