# 题目
You're now a baseball game point recorder. 
Given a list of strings, each string can be one of the 4 following types: 
Integer (one round's score): Directly represents the number of points you get in this round.\
"+" (one round's score): Represents that the points you get in this round are the sum of the last two valid round's points.\
"D" (one round's score): Represents that the points you get in this round are the doubled data of the last valid round's points.\
"C" (an operation, which isn't a round's score): Represents the last valid round's points you get were invalid and should be removed.

Each round's operation is permanent and could have an impact on the round before and the round after. 
You need to return the sum of the points you could get in all the rounds.\
给定一个字符串列表，每个字符串可以是以下4种类型之一:\
整数:直接表示你在这一轮中得到的点数。\
“+”(一个回合的分数):表示你在这一轮中得到的分数是最后两个有效回合点数之和。\
“D”:表示你在这一轮中得到的分数是最后一个有效整数点的两倍数据。\
“C”(一个操作):代表你得到的最后一个有效回合的点数是无效的，并且应该被移除。\
每轮的操作都是永久性的，可能会对前后的回合产生影响。\
你需要返回所有回合中可以得到的点的和。
# 样例输出
Example 1:
Input: ["5","2","C","D","+"]
Output: 30
Explanation: \
Round 1: You could get 5 points. The sum is: 5.\
Round 2: You could get 2 points. The sum is: 7.\
Operation 1: The round 2's data was invalid. The sum is: 5.  \
Round 3: You could get 10 points (the round 2's data has been removed). The sum is: 15.\
Round 4: You could get 5 + 10 = 15 points. The sum is: 30.

Example 2:\
Input: ["5","-2","4","C","D","9","+","+"]\
Output: 27\
Explanation: \
Round 1: You could get 5 points. The sum is: 5.\
Round 2: You could get -2 points. The sum is: 3.\
Round 3: You could get 4 points. The sum is: 7.\
Operation 1: The round 3's data is invalid. The sum is: 3.  \
Round 4: You could get -4 points (the round 3's data has been removed). The sum is: -1.\
Round 5: You could get 9 points. The sum is: 8.\
Round 6: You could get -4 + 9 = 5 points. The sum is 13.\
Round 7: You could get 9 + 5 = 14 points. The sum is 27.
# 分析
* vector容器法：用一个容器来存放得分情况，遍历记录得分的容器，若有C,D出现则对应的对vector容器进行相应的删除元素或者对得分情况进行加倍或求和处理即可。
* stack栈法：和vector类似，只是vector是从尾部记录，而stack从头部入栈记录即可。
# 程序实现
```cpp
class Solution {
public:
    int calPoints(vector<string>& ops) {
       vector<int> con;
    int sum = 0;
        int score = 0;
    for(int i = 0;i<ops.size();i++)
    {
        
        if (ops[i] == "D")
        {
             score = con.back() * 2;
            sum += score;
        }
        else if (ops[i] == "C")
        {
            sum -= con.back();
            con.pop_back();
            continue;
        }
        else if (ops[i] == "+"){
            score = con.back() + con[con.size() - 2];
            sum += score;
        }
        else{
            score=stoi(ops[i]);
            sum+=score;
        }
        con.push_back(score);
    }

    return sum;
}
};