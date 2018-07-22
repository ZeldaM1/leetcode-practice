# 题目
You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.

Write a function to return a hint according to the secret number and friend's guess, use A to indicate the bulls and B to indicate the cows. 

Please note that both secret number and friend's guess may contain duplicate digits.


# 样例输出
Example 1:

Input: secret = "1807", guess = "7810"

Output: "1A3B"

Explanation: 1 bull and 3 cows. The bull is 8, the cows are 0, 1 and 7.
Example 2:

Input: secret = "1123", guess = "0111"

Output: "1A1B"

Explanation: The 1st 1 in friend's guess is a bull, the 2nd or 3rd 1 is a cow.
# 分析
本题可以用hash map来做，也可以用两个数组来做，我采用的是后者。
* for循环求的相同数（即bull的数目）
* 建立两个大小为10的数组a，b，并初始化为0，在相应位置储存两个人说话内容，然后对应的位置取得最小值与cow相加即可
# 程序实现
```cpp
class Solution {
public:
    string getHint(string secret, string guess) {
      int len=secret.length();
        int bull=0,cow=0;
        int a[10]={0},b[10]={0};
       for(int i=0;i<len;i++){
           if(secret[i]==guess[i])
               bull++;
           a[secret[i]-'0']++;
           b[guess[i]-'0']++;
       }
        for(int i=0;i<10;i++)
        cow+=min(a[i],b[i]);
       cow-=bull;
        string result=(to_string(bull)+'A'+to_string(cow)+'B');
        return result;
    }
};
```
* 注意：在用数组储存内容时需要-'0',否则会超时