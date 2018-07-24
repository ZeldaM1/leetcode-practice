# 题目
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.
# 样例输出
Input: [1,8,6,2,5,4,8,3,7]\
Output: 49
# 分析
设置两块板left，right来形成容器，设置water来储存当前最大水量。若left板高度大于right板，则使得right板左移，否则left板向右移。一直使得water取最大值。直到两块板移动到中间位置，
# 程序实现
```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
     int water=0;
        int left=0;
        int right=height.size()-1;
        while(left<right){
            
            water=max(min(height[left],height[right])*(right-left),water);
            
          if( height[left]>height[right])
              right--;
            else
                left++;
          
        }
        return water;
    }
};