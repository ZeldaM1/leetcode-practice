# 题目
Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.\
输出n个数中k的数的不重复排列。
# 样例输出
Example:

Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
# 分析
遍历时取得k个数的方法和subset一样，采取回溯法，但是特别要注意的是要区分相同的元素不同的排列的情况，所以在判断时新增一个if来使得当前数组呈递增数列，再进行判断。
# 程序实现
```cpp
void combi(int x,int y,int z,vector<vector<int>>&a,vector<int>c){
    if(c.size()==z)
    {
       a.push_back(c);
        return;
    }
    if (c.size() > 1 && c.back() < *(c.end()-2))//递增  
            return;
    for(int i=x;i<y;i++){
        c.push_back(i+1);
        combi(i+1,y,z,a,c);
        c.pop_back();
    }
}
class Solution {
public:
    vector<vector<int>> combine(int n, int k) {
            vector<vector<int>>a;
        vector<int>c;
        combi(0,n,k,a,c);
        return a;
    }
};
