# 题目
Initially on a notepad only one character 'A' is present. You can perform two operations on this notepad for each step: \
Copy All: You can copy all the characters present on the notepad (partial copy is not allowed).\
Paste: You can paste the characters which are copied last time.\
Given a number n. You have to get exactly n 'A' on the notepad by performing the minimum number of steps permitted. Output the minimum number of steps to get n 'A'. \
Note:\
The n will be in the range [1, 1000].\
最初只有一个A，每次只能进行复制和粘贴的其中一个操作，现在给定一个数n，求出得到n个A所需进行的最少的操作次数。
# 样例输出
Example 1:\
Input: 3\
Output: 3\
Explanation:\
Intitally, we have one character 'A'.\
In step 1, we use Copy All operation.\
In step 2, we use Paste operation to get 'AA'.\
In step 3, we use Paste operation to get 'AAA'.
# 分析
把前几项列出来可知：\
n=2 time=2\
n=3 time=3\
n=4 time=4\
n=5 time=5\
n=6 time=5
* 则可找到这样规律，以前三项为基础，若能整除3，4或5，则后面n个A所需操作数为n/可整除的数+该数对应的time值，否则等于n本身。
* 递归算法：以2对应的两次为基础，把n/2作为参数带入，找到相应的值然后加上n/2和2即可。
# 程序实现
* 找规律：
```cpp
class Solution {
public:
    int minSteps(int n) {
        vector<int> Min(n,0);
        for (int i = 2; i <n+1; i++) {
            Min[i] = i;
        }
           if(n<=4)
               return Min[n];
        for (int i = 5; i <n+1; ++i) {
            for (int j =2; j<i;j++) {
                if (i % j == 0) {
                    Min[i] = min(Min[i], Min[j]+i/j);
                    break;
                }
            }
        }
        return Min[n];
    }
};
```
* 递归
```cpp
class Solution {
public:
    int minSteps(int n) {
        vector<int>Min(n,0);
        for(int i=2;i<=n;i++)
            Min[i]=i;
        if(n<=4)
            return Min[n];
    int m=n/2;
        Min[n]=min(Min[n],minSteps(m)+n%2+2);
            return Min[n];
    }
};

