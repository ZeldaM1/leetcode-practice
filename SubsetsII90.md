# 题目
Given a collection of integers that might contain duplicates, nums, return all possible subsets (the power set).\
Note: The solution set must not contain duplicate subsets.\
返回所有可能的子集。
注意:不能包含重复的子集。
# 样例输出
Example:

Input: [1,2,2]\
Output:\
[\
  [2],\
  [1],\
  [1,2,2],\
  [2,2],\
  [1,2],\
  []\
]
# 分析
思路和78题相同，只是需要注意在遍历数组时要排除相同子列，则可以再设定一个for循环，用来寻找和当前的数列不同个元素即可。或者在a中查找是否有b的存在，若没有则可以将b放到a中
# 程序实现
* 回溯操作：
```cpp
void find(int x,vector<int>& nums,vector<vector<int>>& a,vector<int>& b){
    if(x==nums.size())
    return ;
   for(int i=x;i<nums.size();i++){
       if(i>x&&nums[i-1]==nums[i])
           continue;//强制跳过当前位置，开始下一次循环
           /* vector<vector<int>>::iterator p=find(a.begin(),a.end(),b);
       if(p==a.end())
           a.push_back(b);*/ //查找重复元素的另一种方法，但是效率会低很多。
   b.push_back(nums[i]);
           a.push_back(b);
       find(i+1,nums,a,b); 
       b.pop_back();
   }
}

class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
         vector<vector<int>>a;
        vector<int>b;
         vector<int>current={};
        a.push_back(b);
        sort(nums.begin(),nums.end());
        find(0,nums,a,b);
        return a;
    }
};
```

* 单纯的for循环只能求出连续的子集:
```
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>>a;
        vector<int>b;
         vector<int>current={};
        if(nums.empty())
        {
            a.push_back(nums);
            return a;
        }
        sort(nums.begin(),nums.end());
        int n=1;
    while(n<=nums.size()){
        for(int i=0;i<nums.size()-n;i++){//起点位置
            int x=0;
           for(int j=i;x<n;j++){//遍历，x记录当前b中个数
               b.push_back(nums[j]);
                     x++;
           }
           if(b!=current)
               a.push_back(b);
           current=b;
           b.clear();
       }  
    n++;
    }
        a.push_back(b);
        return a;
    }
};

