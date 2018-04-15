# 题目
Given a linked list, swap every two adjacent nodes and return its head.\
Note:\
Your algorithm should use only constant extra space.\
You may not modify the values in the list's nodes, only nodes itself may be changed.
# 样例输出
Example:\
Given 1->2->3->4, you should return the list as 2->1->4->3.
# 分析
# 程序实现
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *    int val;
 *    ListNode* next;
 *    ListNode(int x): val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        if(head == NULL) return NULL;
        if(head->next == NULL) return head;

        ListNode* temp = head->next;
        head->next = swapPairs(temp->next);
        temp->next = head;

        return temp;
    }
};
