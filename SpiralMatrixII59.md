# 题目
Given a positive integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.\
给定一个数，输出其回形文字。
# 样例输出
Example:

Input: 3\
Output:\
[\
 [ 1, 2, 3 ],\
 [ 8, 9, 4 ],\
 [ 7, 6, 5 ]\
]
# 分析
其实就是跟着回形的路线走，把二维数组填上对应的数字即可。
# 程序实现
```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
 if(n==0)return vector<vector<int> >();
        vector<vector<int> >result(n, vector<int>(n,0));
        int p = 1;
        int x = 0, y = 0;
        while(p <=n * n){
            while(y < n && result[x][y] == 0) {
                result[x][y] = p;
                y++;
                p++;
            }
            y--;
            x++;
            while(x < n && result[x][y] == 0) {
                result[x][y] = p;
                x++;
                p++;
            }
            x--;
            y--;
            while(y >= 0 && result[x][y] == 0) {
                result[x][y] = p;
                y--;
                p++;
            }
            x--;
            y++;
            while(x >= 0 && result[x][y] == 0 ) {
                result[x][y] = p;
                x--;
                p++;
            }
            x++;
            y++;
        }
        return result;
    }
};