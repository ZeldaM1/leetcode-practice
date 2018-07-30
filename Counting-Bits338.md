# 题目
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.\
Follow up:
* It is very easy to come up with a solution with run time O(n*sizeof(integer)). But can you do it in linear time O(n) /possibly in a single pass?Space complexity should be O(n).
* Can you do it like a boss? Do it without using any builtin function like __builtin_popcount in c++ or in any other language.
# 样例输出
Example:\
For num = 5 you should return [0,1,1,2,1,2].
# 分析
solution1:
设定一个函数来计算对应数字二进制1的个数\
solution2:\
规律：\
[0,1,1,2,1,2,2,3,1,2,2,3...]每后一位都是从数组的第一位开始往后+1得到
# 程序实现
* 72ms:
```cpp
class Solution {
public:
    vector<int> countBits(int num) {
       vector<int> a;
        for(int i=0;i<=num;i++){
            int b=findbit(i);
            a.push_back(b);
        }
        return a;
    }
        
    int findbit(int con){
        int all=0;
        
        while(con!=0){
            int rest=con%2;
            if(rest==1)
                all++;
            con=(con-rest)/2;
            
        }
        return all;
    }
};
```
* 44ms:
```cpp
class Solution {
public:
    vector<int> countBits(int num) {
       vector<int> a(1,0);
        int i=0;
        while(i<num){
            int size=a.size();
           for(int j=0;j<size&&i<num;++j,++i){
           a.push_back(a[j]+1);
              
           }
        }
        return a;
    }
};
  
  