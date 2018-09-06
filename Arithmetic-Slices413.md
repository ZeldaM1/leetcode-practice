# 题目
A sequence of number is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

For example, these are arithmetic sequence:

1, 3, 5, 7, 9
7, 7, 7, 7
3, -1, -5, -9

The following sequence is not arithmetic.

1, 1, 2, 5, 7


A zero-indexed array A consisting of N numbers is given. A slice of that array is any pair of integers (P, Q) such that 0 <= P < Q < N.

A slice (P, Q) of array A is called arithmetic if the sequence:
A[P], A[p + 1], ..., A[Q - 1], A[Q] is arithmetic. In particular, this means that P + 1 < Q.

The function should return the number of arithmetic slices in the array A.
# 样例输出
Example:

A = [1, 2, 3, 4]

return: 3, for 3 arithmetic slices in A: [1, 2, 3], [2, 3, 4] and [1, 2, 3, 4] itself.
# 分析
动态规划：从第三个数开始，计算前两个数的差值是否为定值，是的话则在总的数量上加1\
递归糊成一坨。。。。
# 程序实现
```cpp
class Solution {
public:
    int numberOfArithmeticSlices(vector<int>& A) {
        vector<int>dis(A.size());
        int sum=0;
        for (int i = 2; i < dis.size(); i++) {
            if (A[i] - A[i - 1] == A[i - 1] - A[i - 2]) {
                dis[i] = 1 + dis[i - 1];
                sum += dis[i];
            }
        }
        return sum;
    }
};
```
```cpp
class Solution {
public:
    int all=0,all1=0;
    int sum;
    int numberOfArithmeticSlices(vector<int>& A) {
        sum=2;
        if(A.size()<3)
            return 0;
        vector<int>::iterator p=A.begin();
            p=p+2;
        for(int i=2;i<A.size();i++,p++){
            if(A[i]-A[i-1]==A[i-1]-A[i-2])
            {
                sum++;
               if(sum>=3)
        all1=(sum*sum-3*sum+2)/2;
            }
            else 
                break;
        }
         all+=all1;
        if(p!=A.end()){
        A.erase(A.begin(),p);
            numberOfArithmeticSlices(A);
            }
        
        return all;
    }
};
```
