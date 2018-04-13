# 题目
Given a non-negative integer num represented as a string, remove k digits from the number so that the new number is the smallest possible.
Note:\
The length of num is less than 10002 and will be ≥ k.\
The given num does not contain any leading zero.
# 样例输出
Example 1: \
Input: num = "1432219", k = 3\
Output: "1219"\
Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.

Example 2: \
Input: num = "10200", k = 1\
Output: "200"\
Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

Example 3: \
Input: num = "10", k = 2\
Output: "0"\
Explanation: Remove all the digits from the number and it is left with nothing which is 0.
# 分析
两种想法：
1. 把string类的转换成int型数组A，用另一个数组B来保存A的内容，对数组A进行排序然后取最大的三个数，在数组B中从头遍历数组寻找三个数中的一个元素（数值大的优先），找到即删除该位置元素，最后将数组转为string即可。超时了。。
2. 设定一个string类的num2，使得num2和num相同并将num2入栈，利用auto val: num指令来遍历num的子列，如果发现num子列val中的数大于num2的栈底元素，则将栈底删除，然后将val压入栈底即可，这样保证了栈中元素小于num中的元素。最后取栈中的前nums.size()-k个元素即可。
# 程序实现
```cpp
class Solution {
public:
    string removeKdigits(string num, int k) {
        string num2;
        int n=k;int m=num.size();
        int i=0;
         for(auto val: num)  
        {
             while(num2.size()>0&&val<num2.back()&&n>0){
                 num2.pop_back();
                 n--;
             }
             num2.push_back(val);
         }
        while(num2[i]=='0')
            i++;
        num2=num2.substr(i,m-i-k);
        if(num2.size()!=0)
        return !num2.size()?"0":num2;
    }  
}; 
```
# 总结
之前做栈的时候都要声明stack<类型>名称，第一次看见栈可以用来比较字符类的并且没有声明直接使用，长见识了。
最后取num2元素的时候要判断所需的位置前面是否为0，否则会超时，返回num2时我用的return num2然后超时了，要对num2的大小进行判断然后才判断该返回的值。
