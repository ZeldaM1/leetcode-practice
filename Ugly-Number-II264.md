# 题目
Write a program to find the n-th ugly number. 
Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. \
Note that 1 is typically treated as an ugly number, and n does not exceed 1690\
编写一个程序来查找第n个丑数。\
丑数是正数，其主要因数只有2、3、5。例如，1 2 3 4 5 6 8 9 10 12是前10个丑陋数字的序列。\
注意，1通常被视为一个丑数，而n不超过1690。
# 样例输出
For example, 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.\
# 分析
由于丑数因数只有2 3 5，故丑数表达式可写为2^a*3^b*5^c，然后可以设置三个for循环来找到对应的丑数，但这样的做法超时了并且不能达到寻找
# 程序实现
```cpp
class Solution {
public:
    int nthUglyNumber(int n) {
         vector<int> vec{1};  
        int ith2 = 0, ith3 = 0, ith5 = 0;  
        while(--n > 0)  
        {  
            int val = min(vec[ith2]*2, min(vec[ith3]*3, vec[ith5]*5));  
            vec.push_back(val);  
            while(vec[ith2]*2 <= val) ith2++;  
            while(vec[ith3]*3 <= val) ith3++;  
            while(vec[ith5]*5 <= val) ith5++;  
        }  
        return vec.back();  
    }  
};  
