# 题目
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:\
Integers in each row are sorted from left to right.
The first integer of each row is greater than the last integer of the previous row.\
在一个二维数组中找到目标值。
# 样例输出
Example 1:

Input:\
matrix = [\
  [1,   3,  5,  7],\
  [10, 11, 16, 20],\
  [23, 30, 34, 50]\
]\
target = 3\
Output: true\
Example 2:

Input:\
matrix = [\
  [1,   3,  5,  7],\
  [10, 11, 16, 20],\
  [23, 30, 34, 50]\
]\
target = 13\
Output: false\
class Solution {
# 分析
* solution1：单纯的遍历matrix数组以寻找目标值（14ms）
* solution2：折半查找（12ms）
# 程序实现
* 14ms
```cpp
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        for(int i=0;i<matrix.size();i++){
            for(int j=0;j<matrix[i].size();j++)
                if(matrix[i][j]==target)
                    return true;
        }
        return false;
    }
};
```
* 12ms
```
bool searchMatrix(vector<vector<int>>& matrix, int target) 
{
	if (matrix.empty())	return false;
	int m = matrix.size(), n = matrix[0].size();
	int left = 0, right = m*n-1;
	while (left <= right)
	{
		int mid = (left + right) / 2,i=mid/n,j=mid%n;
		if (matrix[i][j] == target)	return true;
		else if (matrix[i][j] < target)	left = mid + 1;
		else right = mid - 1;
	}
	return false;
}
};