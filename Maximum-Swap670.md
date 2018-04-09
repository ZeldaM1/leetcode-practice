# 题目
Given a non-negative integer, 
you could swap two digits at most once to get the maximum valued number. Return the maximum valued number you could get. \
给定一个非负整数，最多可以交换两个数字，以得到最大值。返回你能得到的最大值。\
Note:\
The given number is in the range [0, 108]
# 样例输出
Example 1:
Input: 2736
Output: 7236
Explanation: Swap the number 2 and the number 7.

Example 2:
Input: 9973
Output: 9973
Explanation: No swap.
# 分析
可以先将int转化为数组（倒序）类型，然后将数组转为顺序，
在数组中找到最大值，然后与数组中的第一个数（也可能是后面几个数中的其中一个）交换，然后转为int输出即可。
# 程序实现
```cpp
class Solution {
public:
    int trans(int* nums, int n){
        int res = 0;
        for(int i=0; i<n; i++){
            res = res*10 + nums[i];
        }
        return res;//定义数组转int函数
    }
    int maximumSwap(int num) {
        int nums[20] = {0};
        int m = num, n = 0;
        while(m){
            nums[n] = m % 10;
           m= m/10;
            n++;
        }//将int转为数组
        for(int i=0, j=n-1; i<j; i++, j--)
            swap(nums[i],nums[j]);//将数组转为顺序
        for(int i=0; i<n; i++){
            int max = nums[i];
            int x = i;
            for(int j=i+1; j<n; j++){
                if(nums[j] >= max){
                    x = j;
                    max = nums[j];
                }
            }//寻找数组中的最大数值
            if(max > nums[i]){
                swap(nums[i], nums[x]);//交换
                return trans(nums, n);
            }
        }
        return num;
    }
};
```
# 总结
看到题本来想用ito将int转化为数组，然后发现自定义转化函数也比较简单
