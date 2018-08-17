# 题目
We are playing the Guess Game. The game is as follows:

I pick a number from 1 to n. You have to guess which number I picked.

Every time you guess wrong, I'll tell you whether the number is higher or lower.

You call a pre-defined API guess(int num) which returns 3 possible results (-1, 1, or 0):

-1 : My number is lower
 1 : My number is higher
 0 : Congrats! You got it!
# 样例输出
Example:

n = 10, I pick 6.

Return 6.
# 分析
二分法逐步缩小范围即可
# 程序实现
```cpp
// Forward declaration of guess API.
// @param num, your guess
// @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
int guess(int num);

class Solution {
public:
    int guessNumber(int n) {
        int a=1,b=n,c,d;
        while(a<=b){
            c=a+(b-a)/2;
            d=guess(c);
            if(d==0)
                return c;
                else if(d==-1)
                    b=c-1;
                    else 
                       a=c+1;
        }
        return -1;
    }
    
};
```
