# 题目
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

Note: m and n will be at most 100.
# 样例输出
Example 1:\
Input:\
[\
  [0,0,0],\
  [0,1,0],\
  [0,0,0]\
]\
Output: 2\
Explanation:\
There is one obstacle in the middle of the 3x3 grid above.\
There are two ways to reach the bottom-right corner:\
1. Right -> Right -> Down -> Down\
2. Down -> Down -> Right -> Right
# 分析
和之前unique paths一样，只是遍历时需考虑当前位置是否为1，若为1则当前位置的数字置零
# 程序实现
```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m=obstacleGrid.size();
        int n=obstacleGrid[0].size();
        int i,j;
        if(m==1||n==1)//考虑一行一列的情况
            {
            int all=0;
            if(obstacleGrid[0][0]==1)
                return 0;
            for(i=0;i<m;i++){
            for(j=0;j<n;j++){
                all+=obstacleGrid[i][j];
            }
            }
            if(all==0)
                return 1;
            else 
                return 0;
        }
        else if(m>1&&n>1){
       vector<vector<int>>&a= obstacleGrid;//多行多列
        if(a[0][0]==1)
                return 0;
        for(i=1;i<m;i++)
        {
            if(a[i][0]==0)
            a[i][0]=1;
            else if(a[i][0]==1)
            {
                for(int k=i;k<m;k++)
                    a[k][0]=0;
            }
        }
            
         for(j=1;j<n;j++)
            {
              if(a[0][j]==0)
            a[0][j]=1;
            else if(a[0][j]==1)
            {
                for(int k=j;k<n;k++)
                    a[0][k]=0;
            }
         }
          for(i=1;i<m;i++){
            for(j=1;j<n;j++){
                if(a[i][j]==0)
                a[i][j]=a[i-1][j]+a[i][j-1];
                else if(a[i][j]==1)
                    a[i][j]=0;
            }
        }
        return a[m-1][n-1];
        }
    }
};
```