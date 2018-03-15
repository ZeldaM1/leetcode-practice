# 题目
Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.
Note:
Bonus point if you are able to do this using only O(n) extra space, where n is the total number of rows in the triangle.
给定一个三角形，从上到下找到最小路径和。每一步都可以移动到下面一行的邻接数字。
# 案列
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11). 
# 分析
可以将数组从下至上遍历，每次获得相对应的值后再比较上一层相邻数字的大小并取较小值，直至遍历完成后返回最小值
# 代码
```
class Solution {
public:
    int minimumTotal(vector<vector<int> > &triangle) {
        vector<int> min = triangle[triangle.size() - 1];
        for (int i = triangle.size() - 2; i > - 1; --i)
          for (int j = 0; j <= i; ++j)
                min[j] = (min[j] < min[j + 1] ? min[j] : min[j + 1])  + triangle[i][j];
        return min[0];
    }
如果本题只是单纯求最小数字，做法如下：
class Solution {
public:
    int minimumTotal(vector<vector<int> > &triangle) {
        int n=triangle.size(),min=0;//n为行数
       for(int i=0;i<n;i++)
       {
       int m=triangle[i].size();//m为每行列数
               if(m>0)
               {
           for(int j=0;j<m-1;j++)
           {
               for(int k=0;k<m-1-j;k++)
               {
                   if(triangle[i][k]>triangle[i][k+1])
                   {
                       int temp=triangle[i][k];
                       triangle[i][k]=triangle[i][k+1];
                       triangle[i][k+1]=temp;
                   }
               }
       }//对每行数据进行冒泡排序使每行数据从小到大排列
       }
       }
        for(int i=0;i<n;i++)
        {
           min+=triangle[i][0]; 
        }//使每行的第一位数相加之和为最小路径
        return min;
    }
};
