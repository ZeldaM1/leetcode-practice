# 题目
* Given a string s and a string t, check if s is subsequence of t.

* You may assume that there is only lower case English letters in both s and t. t is potentially a very long (length ~= 500,000) string, and s is a short string (<=100).

* A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, "ace" is a subsequence of "abcde" while "aec" is not).
* Follow up:\
If there are lots of incoming S, say S1, S2, ... , Sk where k >= 1B, and you want to check one by one to see if T has its subsequence. In this scenario, how would you change your code?
# 样例输出

Example 1:
s = "abc", t = "ahbgdc"

Return true.

Example 2:
s = "axc", t = "ahbgdc"

Return false.

# 分析
* solution1:把t作为主线，遍历t，在s中寻找是否有符合条件的，一直重复，直到遍历s的指针到达s的末端
* solution2：把s作为主线，每次在s中获取一个字符之后在t中寻找这个字符，并且每次在t中寻找时的初始位置都是上一次寻找结束的位置,但是这样耗时太长
# 程序实现
* 48ms:
```cpp
class Solution {
public:
    bool isSubsequence(string s, string t) {
        int i=0,j=0;
        if(s=="")
            return true;
            for(j=0;j<t.size();j++){
                if(t[j]==s[i])
                    i++;
               
                if (i == s.size())
                    return true;
            }
        return false;
        }

};