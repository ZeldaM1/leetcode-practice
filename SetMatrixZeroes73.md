# 题目
Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in-place.\
矩阵置零。
# 样例输出
Example 1:

Input:\
[\
  [1,1,1],\
  [1,0,1],\
  [1,1,1]\
]\
Output: \
[\
  [1,0,1],\
  [0,0,0],\
  [1,0,1]\
]\
Example 2:

Input:\
[\
  [0,1,2,0],\
  [3,4,5,2],\
  [1,3,1,5]\
]\
Output:\
[\
  [0,0,0,0],\
  [0,4,5,0],\
  [0,3,1,0]\
]\
Follow up:

A straight forward solution using O(mn) space is probably a bad idea.\
A simple improvement uses O(m + n) space, but still not the best solution.\
Could you devise a constant space solution?
# 分析
* solution1：将0所在的行和列均置为最小,然后遍历数组将最小的值改为0即可，但是单纯将数字置为最小值的操作不能排除某位数上的数也为INT_MIN的情况。
* solution2：建立两个数组row，col分别记录下数组中相对应的行列的情况，若为0，则该位置对应的两个数组值分别为1，最后对数组进行遍历，若有row或col的值为1则将二维数组该位对应的数改为0即可。
# 程序实现
* solution2：
```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
      int row[matrix.size()]={0},col[matrix[0].size()]={0};
   
    for(int i=0;i<matrix.size();i++)
    {
        for(int j=0;j<matrix[0].size();j++)
        {
            if(matrix[i][j]==0)
            {
                row[i]=1;
                col[j]=1;
            }
        }
    }
    for(int i=0;i<matrix.size();i++)
    {
        for(int j=0;j<matrix[0].size();j++)
        {
            if(row[i]==1||col[j]==1)
            {
                matrix[i][j]=0;
            }
        }
    }
}

};
```
* solution1:
```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
       for(int i=0;i<matrix.size();i++){
          for(int j=0;j<matrix[i].size();j++)
          {
              if(matrix[i][j]==0){
           for(int m=0;m<matrix[i].size();m++)
           {
               if(matrix[i][m]!=0)
            matrix[i][m]=INT_MIN;          
           }
              
        for(int m=0;m<matrix.size();m++)
        {
            if(matrix[m][j]!=0)
                matrix[m][j]=INT_MIN;
        }
              }
          }
       }
        for(int i=0;i<matrix.size();i++){
          for(int j=0;j<matrix[i].size();j++)
          {
              if(matrix[i][j]==INT_MIN)
                 matrix[i][j]=0;
    }
    }
    }
};
