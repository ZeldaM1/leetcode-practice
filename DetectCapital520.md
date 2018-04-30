# 题目
Given a word, you need to judge whether the usage of capitals in it is right or not. \
We define the usage of capitals in a word to be right when one of the following cases holds: \
All letters in this word are capitals, like "USA".\
All letters in this word are not capitals, like "leetcode".\
Only the first letter in this word is capital if it has more than one letter, like "Google".\
Otherwise, we define that this word doesn't use capitals in a right way. \
Note: The input will be a non-empty word consisting of uppercase and lowercase latin letters. \
给定一个词，你需要判断它的使用是否正确。
当下列情形之一成立时，我们定义大写字母的用法:
* 这个词的所有字母都是大写的，像“USA”。
* 这个词的所有字母都不是大写字母，像“leetcode”。
* 只有第一个字母是大写的，如果它有多个字母，比如“Google”。
否则，我们定义这个单词不使用正确的大写。
注意:输入将是一个非空词，由大写字母和小写拉丁字母组成。
# 样例输出
Example 1:
Input: "USA"
Output: True

Example 2:
Input: "FlaG"
Output: False
# 分析
string里有islower和isupper函数来判断当前元素是否是大写或者小写，则可以从第一个字符入手，讨论两种情况：1.第一个字符为大写或小写，第二个为小写，然后依次判断后续的字符中是否有大写的情况。2：字符全为大写。此时则遍历string字符串，若发现有小写的则返回false即可。
# 程序实现
```cpp
class Solution {
public:
    bool detectCapitalUse(string word) {
    if (word.length() <= 1) 
        return true;
        if (islower(word[0]) || (isupper(word[0]) && islower(word[1])))
        {
            for (int i = 1; i < word.length(); i++)
                if (isupper(word[i])) 
                    return false;
        } 
        else
        {
            for (int i = 1; i < word.length(); i++)
                if (islower(word[i])) 
                    return false;
        }
        return true;
    }
};