# 题目
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:
* Integers in each row are sorted in ascending from left to right.
* Integers in each column are sorted in ascending from top to bottom.
# 样例输出
Example:

Consider the following matrix:\
[\
  [1,   4,  7, 11, 15],\
  [2,   5,  8, 12, 19],\
  [3,   6,  9, 16, 22],\
  [10, 13, 14, 17, 24],\
  [18, 21, 23, 26, 30]\
]\
Given target = 5, return true.\
Given target = 20, return false.
# 分析
* 滑动窗口法：\
设定一大小可变化的滑动窗口依次遍历矩阵直到找到符合条件的窗口（runtime error）
* 从矩阵的右上角向左下角遍历，若得到等于target的数则返回true，否则判断当前数值是否大于target（满足排序条件否？），不满足则继续向下一行遍历数组
# 程序实现
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
      if(matrix.size()==0||matrix[0].size()==0)
          return false;
        int i=0, j=matrix[0].size()-1;
        while(i<matrix.size() && j>=0) {
            int x = matrix[i][j];
            if(target == x) 
                return true;
            else if(target < x) 
                j--;
            else 
                i++;
        }
        return false;
    }
};
```
* 若题目改为：寻找一个以target为中心的矩阵，使得矩阵满足如上条件。则可以写成如下形式：
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if(matrix.size()==0)
            return false;
        int matrix2[matrix.size()+2][matrix[0].size()+2]={0};
        for(int i=1;i<=matrix.size();i++)
        {
            for(int j=1;j<=matrix[0].size();j++){
            matrix2[i][j]=matrix[i-1][j-1];
            }
        }
        for(int i=1;i<=matrix.size();i++){
            for(int j=1;j<=matrix[0].size();j++){
                if(matrix2[i][j]==target)
                {
                    int a1=matrix2[i-1][j-1],a2=matrix2[i-1][j],a3=matrix2[i-1][j+1];
                    int a4=matrix2[i][j-1],a5=matrix2[i][j],a6=matrix2[i][j+1];
                    int a7=matrix2[i+1][j-1],a8=matrix2[i+1][j],a9=matrix2[i+1][j+1];
                    if(a1<=a2<=a3&&a4<=a5<=a6&&a7<=a8<=a9&&a1<=a4<=a7&&a2<=a5<=a8&&a3<=a6<=a9)
                        return true;
                }
            }
        }
        return false;
    }
};
        
        
   