# 题目
Given an array consists of non-negative integers, your task is to count the number of triplets chosen from the array that can make triangles if we take them as side lengths of a triangle.\
Note:\
* The length of the given array won't exceed 1000.
* The integers in the given array are in the range of [0, 1000].
# 样例输出
Example 1:\
Input: [2,2,3,4]\
Output: 3\
Explanation:\
Valid combinations are:\ 
2,3,4 (using the first 2)\
2,3,4 (using the second 2)\
2,2,3
# 分析
由于不同位置的相同数字组成的三角形也被视为不同的三角形，故不需要考虑重复问题。只需要对数组排序，然后遍历数组，判断前两个数之和是否大于第三个数即可（三角形两小边之和大于第三边）
# 程序实现
```cpp
class Solution {
public:
    int triangleNumber(vector<int>& nums) {
        if(nums.size()<3)
            return 0;
        sort(nums.begin(),nums.end()); 
        int all=0;
        for(int i=0;i<nums.size()-2;i++){
            for(int j=i+1;j<nums.size()-1;j++){
                for(int k=j+1;k<nums.size();k++){
                    if((nums[i]+nums[j])>nums[k]){
                        all++;
                    }      
            }
        }
    }
        return all;
    }
};



