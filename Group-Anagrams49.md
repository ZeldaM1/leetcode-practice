# 题目
Given an array of strings, group anagrams together.
* Note:

    All inputs will be in lowercase.
    The order of your output does not matter.


# 样例输出
Example:

Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]

# 分析
* runtime error:
设定容器b来存放最终结果，容器a来对给定内容进行排序和分类。遍历strs，并使得a等于strs，然后对a的每一个元素进行排序，此后遍历a，若当前项和前一项相等则向b中放入strs对应位置的元素。
* ac:
用一个map来存放对应的元素及其同根元素。
# 程序实现
* runtime error:
```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
    vector<vector<string>>b;
    if (strs.empty())
            return b;
        vector<string>& a=strs;
        int j=0;
        sort(a[0].begin(),a[0].end());
        b[0].push_back(a[0]);
        for(int i=1;i<strs.size();i++)
        {
            sort(a[i].begin(),a[i].end());
                if(a[i]==a[i-1])
                    b[j].push_back(strs[i]);
                else{
                    j++;
                    b[j].push_back(strs[i]);
                    
                }
            }
        return b;           
    }
};
```
* ac:
```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string> > a;
        if (strs.empty())
            return a;
        sort(strs.begin(), strs.end());
        map<string, vector<string>> mp;

        for (int i = 0; i < strs.size(); i++)
        {
            string str = strs[i];
            sort(str.begin(), str.end());
            mp[str].push_back(strs[i]);
        }
        for (map<string, vector<string> >::iterator p = mp.begin(); p!= mp.end(); p++)
            a.push_back(p->second);

        return a;
    }
};
