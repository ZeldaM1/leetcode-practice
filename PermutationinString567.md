# 题目
Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1.\
In other words, one of the first string's permutations is the substring of the second string.\
Note:\
The input strings only contain lower case letters.\
The length of both given strings is in range [1, 10,000].\
判断s2的子列中是否有s1的某个排列。
# 样例输出
Example 1:\
Input:s1 = "ab" s2 = "eidbaooo"\
Output:True\
Explanation: s2 contains one permutation of s1 ("ba").

Example 2:\
Input:s1= "ab" s2 = "eidboaoo"\
Output: False
# 分析
* 超时的思路：用一个string类的s3来存放s2中长度等于s1长度的子串，用类似滑动窗口的方法来取得s3，然后对s1，s3进行排序，若s3等于s1，则返回true，否则在整个窗口滑动完毕后返回false。
* ac的思路:也是利用了滑动窗口的思路，但是将s1和s2的长度为s1的子串用长度为26的vector容器存起来,先将s2的前s1长度的的部分存到vector容器中，然后对m1，m2容器进行比较，若两容器相同则返回true，否则再对s2的剩下部分进行遍历，方法同上。
# 程序实现
* 超时：
```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
     if(s1.size()>s2.size())
         return false;
        int m=s1.size();
        int n=s2.size();
         sort(s1.begin(),s1.end());
        for(int i=0;i<n-m+1;i++){
            string s3=s2.substr(i,m);
            sort(s3.begin(),s3.end());
           
            if(s3==s1)
                return true;
        }
        return false;
    }
};
```
* ac:
```cpp
class Solution {
public:
bool checkInclusion(string s1, string s2) {
    int m = s1.size();
    int n = s2.size();
    if (m > n) return false;
    vector<int> m1(26), m2(26);
    for (int i = 0; i < m; ++i)
    {
        m1[s1[i] - 'a'] ++;
        m2[s2[i] - 'a'] ++;
    }
    if (m1 == m2) return true;
    for (int i = 0; i + m < n; ++i)
{
        m2[s2[i] - 'a'] --;
        m2[s2[i + m] - 'a'] ++;
        if (m1 == m2) return true;
    }
    return false;
}
};
