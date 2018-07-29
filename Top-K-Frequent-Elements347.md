# 题目
 Given a non-empty array of integers, return the k most frequent elements.\
 Note:
* You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
* Your algorithm's time complexity must be better than O(n log n), where n is the array's size.

# 样例输出
For example:\
Given [1,1,1,2,2,3] and k = 2, return [1,2].
# 分析
用一个map来存放对应数字及其次数，一个vector来存放次，然后对vector进行排序，找到前K个次数并在map中找到对应元素即可。
# 程序实现
```cpp
class Solution {
public:

    vector<int> topKFrequent(vector<int>& nums, int k) {
       vector<int>a;
        vector<int>c;
        map<int,int>b;
        sort(nums.begin(),nums.end());
        int time=1;
      
        for(int i=1;i<nums.size();i++){
           if(nums[i]==nums[i-1])
           {
               time++;
           b.insert(pair<int,int>(nums[i],time));
           }
           else  if(nums[i]!=nums[i-1]){
                a.push_back(time);
              
               time=1;
               b.insert(pair<int,int>(nums[i],time));
              
    }
       }
         a.push_back(time);
        sort(a.begin(),a.end());
        reverse(a.begin(),a.end());
        multimap<int,int>:: iterator p;
        for(int j=0;j<k;j++){
            p=b.begin();
            while(p!=b.end()){
                if(p->second==a[j])
                    c.push_back(p->first);
                p++;
            }
                    
    }
        return c;
    }
};