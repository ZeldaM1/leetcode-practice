# 题目
Given scores of N athletes, find their relative ranks and the people with the top three highest scores, who will be awarded medals: "Gold Medal", "Silver Medal" and "Bronze Medal".\
判断金牌得主\
Note:
N is a positive integer and won't exceed 10,000.
All the scores of athletes are guaranteed to be unique.
# 样例输出
Example 1:
Input: [5, 4, 3, 2, 1]
Output: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]
Explanation: The first three athletes got the top three highest scores, so they got "Gold Medal", "Silver Medal" and "Bronze Medal". 
For the left two athletes, you just need to output their relative ranks according to their scores.
# 分析
* solution a：用一个map来存放nums内容，根据map排序的大小进行对second元素的赋值，若为1 2 3则分别给与金银铜牌，否则将排名加入到ma这个容器中，最后返回ma容器
* solution b：设定两个vector来分别存放nums内容和得奖情况，由于题目给出的成绩是连续的，则只需要将存放nums内容的容器排序，然后比较排序后的容器和nums对应位置上的值是否相同即可。


# 程序实现
* solution a：
```cpp
class Solution {
public:
    vector<string> findRelativeRanks(vector<int>& nums) {
        vector<string>ma;
        multimap<int,string>hello;
        for(int i=0;i<nums.size();i++)
            hello.insert(nums[i],0);
        multimap<int,string>::iterator p=hello.begin();
        int n=1;
        while(p!=hello.end()){
            n++;
            p->second=n;
            p++;
        }
        p=hello.begin();
        n=1;
        for(int i=0;i<nums.size();i++){
            int m=nums[i];
            if(ma[m]==1){
                ma.push_back("Gold Medal");
            }
           else  if(ma[m]==2){
                ma.push_back("Silver Medal");
            }
            else if(ma[m]==3){
                ma.push_back("Bronze Medal");
            }
            else
                ma.push_back(to_string(n));
           n++;
        }
        return ma;
    }
};
```
* solution b
```cpp
class Solution {
public:
     vector<string> findRelativeRanks(vector<int>& nums) {
        vector<int> arr = nums;
        auto cmp = [](int a, int b) {return a > b;};
        sort(arr.begin(), arr.end(), cmp);
        vector<string> result(nums.size());
        for (int i = 0; i < nums.size(); i++) {
            for (int j = 0; j < nums.size(); j++) {
                if (nums[i] == arr[j]) {
                    switch(j) {
                        case 0:
                            result[i] = "Gold Medal";
                            break;
                        case 1:
                            result[i] = "Silver Medal";
                            break;
                        case 2:
                            result[i] = "Bronze Medal";
                            break;
                        default:
                            result[i] = to_string(j + 1);
                            break;
                    }
                    break;
                }
            }
        }
        return result;
    }
};