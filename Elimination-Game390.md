# 题目
 There is a list of sorted integers from 1 to n. Starting from left to right, remove the first number and every other number afterward until you reach the end of the list.

Repeat the previous step again, but this time from right to left, remove the right most number and every other number from the remaining numbers.

We keep repeating the steps again, alternating left to right and right to left, until a single number remains.

Find the last number that remains starting with a list of length n.


# 样例输出

Example:

Input:
n = 9,
1 2 3 4 5 6 7 8 9
2 4 6 8
2 6
6

Output:
6
# 分析
soluiton1(runtime error):\
倒水的方法，设置两个栈，不断地在两个栈之来回倒
solution2:\
设置两个数组，不断颠倒数组来回储存
# 程序实现
* solution1:
```cpp
class Solution {
public:
    int lastRemaining(int n) {
        stack<int>a;
        stack<int>b;
        int order=1;
        for(int i=n;i>=1;i--){
            a.push(i);
        }
        while(!a.empty()||!b.empty()){
            if(order%2!=0){
                while(!a.empty()){
                a.pop();
                    b.push(a.top());
                    a.pop();
                }
                 order++;
            }
           
                else if(order%2==0){
                    while(!b.empty()){
                  b.pop();
                    a.push(b.top());
                        b.pop();
                }
                     order++;
            }
           
        }
        if(!a.empty())
            return a.top();
        else
            return b.top();
    
    }
};
```
* solution2:
```cpp
class Solution {
public:
    int lastRemaining(int n) {
       vector<int> a;
        for (int i = 1; i <= n; i++)
            a.push_back(i);
        int flag = true;
        while (a.size()>=2)
        {
            vector<int> b;
            if (flag)
            {
                for (int i = 1; i < a.size(); i+=2)
                    b.push_back(a[i]);
            }
            else
            {
                for (int i = a.size()-2; i >=0 ; i-=2)
                    b.push_back(a[i]);
                reverse(b.begin(),b.end());
            }
            flag = !flag;
            a = b;
        }
        return a[0];
    }
};