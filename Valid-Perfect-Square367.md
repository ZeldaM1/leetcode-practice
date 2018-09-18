# 题目
Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as sqrt.
# 样例输出
Example 1:\
Input: 16\
Output: true

Example 2:\
Input: 14\
Output: false
# 分析
二分法查找
# 程序实现
```cpp
class Solution {
public:
    bool isPerfectSquare(int num) {
        if(num<0)
            return false;
        if(num==0||num==1||num==4||num==9||num==16||num==25||num==36||num==49||num==64||num==81||num==100)
            return true;
        int left=1,right=num;
        double mid;
        while(left<=right){
            mid=(right+left)/2;
            if(mid*mid==num)
                return true;
           else if(mid*mid>num)
            right=int(mid)-1;
                   
          else  if(mid*mid<num)
              left=int(mid)+1;
        }
        return false;
    }
};
```