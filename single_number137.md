# 题目
Given an array of integers, every element appears three times except for one, which appears exactly once. Find that single one. 
Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory? 给定一个整数数组，每个元素会出现三次，除了有一个元素会出现一次，发现这个元素。
注意:
你能在不使用额外内存的情况下实现它吗?
# 分析
本可以用定义两个数组的方法来做，但题目明确要求不占用额外内存，故不能再设置另一个数组来储存结果。前面学到的“或、与、非、异或”此时就可以派上用场了。（然而是看了大神的代码才知道）【捂脸】【捂脸】
# 总结
不能用数组做就很尴尬，考虑到前面的题目，从二进制的数字的形式考虑题目通常会简单很多，比如这道题的位运算和位操作意识就很强。
# 代码
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int a = 0, b = 0;
        for(auto& c : nums)//用c引用nums的内容
      {
            int x = ((~a) & (~b) & c) | (a & (~b) & (~c));
            int y = (a & (~b) & c) | ((~a) & b & (~c));
            a = x;
            b = y;
        }
        return a | b;
    }
};
