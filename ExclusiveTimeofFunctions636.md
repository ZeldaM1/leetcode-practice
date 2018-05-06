# 题目
Given the running logs of n functions that are executed in a nonpreemptive single threaded CPU, find the exclusive time of these functions. 
Each function has a unique id, start from 0 to n-1. A function may be called recursively or by another function.\
计算每个程序单独运行的时间。\
Note:\
Input logs will be sorted by timestamp, NOT log id.\
Your output should be sorted by function id, which means the 0th element of your output corresponds to the exclusive time of function 0.\
Two functions won't start or end at the same time.\
Functions could be called recursively, and will always end.\
1 <= n <= 100
注意：输出结果要按照id排序
# 样例输出
Example 1:\
Input:\
n = 2\
logs = \
["0:start:0",\
 "1:start:2",\
 "1:end:5",\
 "0:end:6"]\
Output:[3, 4]\
# 分析
* 这道题实质上又是一道类似于括号匹配的问题，可以设定一个栈来维持id顺序，一个map来记录相应的id对应的时间，若当前栈顶没有给出的id，则将id入账，将id和id对应的时间记录到map中，而若当前栈顶有相同的id，则使的map中对应的id的时间成为两次id时间之差，然后删除栈顶元素，继续比较直到栈中没有元素即可。\
有个很狗的事情就是我不会用split函数。。
* 然后有个简单的就是用find函数来取得相对应的id和time值和指令cmd，做法和上述类似。
# 程序实现
```cpp
class Solution {
public:
    vector<int> exclusiveTime(int n, vector<string>& logs) {
    	map<int,int>res;
    	stack<int>time;
    	for(int i=0;i<logs.size();i++){
       string a=logs[i].split("//:") ;
       if(*a.begin()==time.top())
	   {
       res[a.begin()]->second=*a.end()-res[a.begin()]->second+1;
       time.pop();
   }
	   else if(*a.begin()!=time.top()){
	   	time.push(*a.begin());
        res.insert(*a.begin(),*a.end());
    }
        }
    map<int,int>::iterator p1=res.begin();
    map<int,int>::iterator p2=p1+1;
    while(p2!=res.end()){
    p1->second-=p2->second;
    p1++;
    p2++;
}
	map<int,int>::iterator p=res.begin();
vector<int,int>left;
while(p!=res.end())
{
left.push_back(*p->first,*p->second);
p++;
}
}
};
```
```cpp
class Solution {
public:
    vector<int> exclusiveTime(int n, vector<string>& logs) {
        vector<int> res(n, 0);
        stack<int> st;
        int preTime = 0;
        for (string log : logs) {
            int found1 = log.find(":");
            int found2 = log.find_last_of(":");
            int idx = stoi(log.substr(0, found1));
            string cmd = log.substr(found1 + 1, found2 - found1 - 1);
            int time = stoi(log.substr(found2 + 1));
            if (!st.empty()) {
                res[st.top()] += time - preTime;
            }
            preTime = time;
            if (cmd== "start") st.push(idx);
            else {
                auto t = st.top(); st.pop();
                ++res[t];
                ++preTime;
            }
        }
        return res;
    }
};


