# 题目
Given two strings s and t, write a function to determine if t is an anagram of s.\
比较两个字符串是否相同。（顺序可以变化，但内容要相同）
Note:\
You may assume the string contains only lowercase alphabets.\
Follow up:\
What if the inputs contain unicode characters? How would you adapt your solution to such case?
# 样例输出
For example:\
s = "anagram", t = "nagaram", return true.\
s = "rat", t = "car", return false.
# 分析
两种思路：
* 利用STL模板库的sort函数对两个字符串进行排序，然后对排序结果进行比较，相同则返回true。
* 将两个字符串的内容分别存到两个multiset容器里面，然后对容器进行遍历，若发现容器相同位置上有不同的元素则返回false。
# 程序实现
```cpp
思路1：
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.empty()&&t.empty())
            return true;
        sort(s.begin(),s.end());
        sort(t.begin(),t.end());
        if(s==t)
            return true;
        else 
            return false;
    }
};
思路2：
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.empty()&&t.empty())
            return false;
        multiset<char>helloo;
        multiset<char>hello2;
        for(auto i=s.begin();i!=s.end();i++)
            helloo.insert(*i);
        for(auto i=t.begin();i!=t.end();i++)
            hello2.insert(*i);
          for(auto j=helloo.begin(),k=hello2.begin();j!=helloo.end(),k!=hello2.end();j++,k++)
          {
              if(*j!=*k)
                  return false;
          }
        return true;
    }
};