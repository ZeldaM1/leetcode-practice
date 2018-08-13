 # 题目
 Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.\
Note:

    The input string length won't exceed 1000
# 样例输出
Example 1:\
Input: "abc"\
Output: 3\
Explanation: Three palindromic strings: "a", "b", "c".

Example 2:\
Input: "aaa"\
Output: 6\
Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
# 程序实现
* solution1:弱鸡解法
```cpp
class Solution {
public:
    int countSubstrings(string s) {
        string a,b;
        int all=0;
        for(int i=1;i<=s.size();i++){
            for(int j=0;j<=s.size()-i;j++){
                a=s.substr(j,i);
                b=a;
                reverse(a.begin(),a.end());
                if(a==b)
                    all++;
            }
        }
        return all;
    }
};
```
* solution2:滑动窗口法
```cpp
class Solution {
public:
    int countSubstrings(string s) {
        int n = s.size(), i = 0, j = 0, count = 0;
        while (j < n) {
            while (j + 1 < n && s[j] == s[j + 1])
                j++;
            int tmp = j + 1, dupLength = j - i + 1;
            count += (1 + dupLength) * dupLength / 2;
            while (i - 1 >= 0 && j + 1 < n && s[i - 1] == s[j + 1]) {
                i--;
                j++;
                count++;
            }
            i = j = tmp;
        }
        return count;
    }
};
```