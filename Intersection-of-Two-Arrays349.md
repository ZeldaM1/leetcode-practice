# 题目
Given two arrays, write a function to compute their intersection.\
Note:

Each element in the result must be unique.
The result can be in any order.
# 样例输出
Example 1:

Input: nums1 = [1,2,2,1,nums2 = [2,2]\
Output: [2]\
Example 2:

Input: nums1 = [4,9,5],nums2 = [9,4,9,8,4]\
Output: [9,4]
# 分析
遍历两个数组，找到重复数字，最后删除重复数字即可。
# 程序实现
```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
         vector<int>a;
        int i=0,j=0;
        vector<int>b;
        if(nums1==nums2)
            return nums1;
        if(nums1.size()==0||nums2.size()==0)
            return b;
       
        while(i<nums1.size()){
            j=0;
            while(j<nums2.size()&&i<nums1.size()){
                if(nums1[i]==nums2[j])
                {
                    a.push_back(nums1[i]);//记录交叉数据
                    i++;
                j++;
                }
                else
                    j++;
            }
             i++;
        }
     b.push_back(a[0]);
        for(int i=1;i<a.size();i++)//查重
        {
            if(a[i]!=a[i-1])
                b.push_back(a[i]);
        }
           return b;  
    }
};
```