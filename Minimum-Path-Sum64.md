# 题目
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.\
Note: You can only move either down or right at any point in time.
# 样例输出
Example:\
Input:\
[
  [1,3,1],\
  [1,5,1],\
  [4,2,1]\
]\
Output: 7\
Explanation: Because the path 1→3→1→1→1 minimizes the sum.
# 分析
动态规划\
每一个数组的最左列数字为从上到下的累加，最上一行数字为从左到右的累加，再从（1,1）开始，第（i,j）位置的最小路径和数可能来自左边或上边的数，故取二者中较小的那一个然后于当前位置数字相加即为当前位置的最小路径和
# 程序实现
```cpp
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        vector<vector<int>>&a=grid;
        int all;
        int i,j;
        for( i=1;i<grid.size();i++)
            a[i][0]+=a[i-1][0];
        for( j=1;j<grid[0].size();j++)
            a[0][j]+=grid[0][j-1];
        for(i=1;i<grid.size();i++){
            for(j=1;j<grid[0].size();j++){
                a[i][j]=min(a[i][j]+a[i-1][j],a[i][j]+a[i][j-1]);
            }
        }
        return a[i-1][j-1];
    }
};
```