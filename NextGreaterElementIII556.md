# 题目
Given a positive 32-bit integer n, you need to find the smallest 32-bit integer which has exactly the same digits existing in the integer n and is greater in value than n. \
If no such positive 32-bit integer exists, you need to return -1.\
寻找相同数字组成的最大值。
# 样例输出
Example 1:\
Input: 12\
Output: 21\
 
Example 2:\
Input: 21\
Output: -1
# 分析
* 思路1：将n的每个位分离出来，存入vector容器里面，然后对容器元素进行排序，从容器底部开始向上累加，每次加完容器底部的元素后删除该元素，直到容器内部没有元素，然后队结果进行判断即可。
* 思路2：先用to_string把int类型的n转化为string类型，然后对string中的元素进行两两比较，使得元素按照从大到小排序，然后用stoi指令将string转为int。
# 程序实现
* 思路1：
```cpp
class Solution {
public:
      int nextGreaterElement(int n) {
        int b;
        int o=n;
        vector<int>a;
        while(n){
            b=n%10;
            n=n/10;
            a.push_back(b);
        }
        sort(a.begin(),a.end());
        int max=0;
      int f;
        while(!a.empty()){
            vector<int>::iterator p=a.end()-1;
            int hello=*p;
            if(a.size()==1)
                f=hello;
            else
            {
                int m=a.size()-1;
            for(int i=0;i<m;i++)
            f=hello*10;
            }
            max+=f;
        a.pop_back();
        }
        
        if(max>o)
           return max;
        else 
            return -1;
    }
};
```
* 思路2：
```cpp
class Solution {
public:
      int nextGreaterElement(int n) {
        string num = to_string(n);  
        int i = num.size()-1;  
          
        while(i && num[i]<=num[i-1]) --i;  
        if(!i) 
            return -1;  
        reverse(num.begin()+i, num.end());  
        for(int j=i; j<num.size(); ++j) {  
            if(num[j] > num[i-1]) {  
                swap(num[j], num[i-1]);  
                break;  
            }  
        }  
          
        if(num.size() == 10 && num > to_string(INT_MAX))   
            return -1;  
          
        return stoi(num);  
    }  
};  