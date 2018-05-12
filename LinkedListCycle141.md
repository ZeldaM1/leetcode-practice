# 题目
Given a linked list, determine if it has a cycle in it. 
Follow up:\
Can you solve it without using extra space? \
判定一个链表内部是否构成环。
# 分析
链表的题好像快慢指针的用处很大，这里可以设定两个指针fast，slow，且fast比slow快（设快了一步），若链表有循环，则进入循环后两个指针会在循环内一直走，直到快指针追上了慢指针，返回true即可。否则就判断链表中当前节点的下一节点是否为空，若为空则返回false。
# 程序实现
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool hasCycle(struct ListNode *head) {    
   struct ListNode* fast=head;
   struct ListNode* slow=head;
    while(fast!=NULL&&slow!=NULL&fast->next!=NULL){
        fast=fast->next->next;
        slow=slow->next;
        if(fast==slow)
            return true;
    }
    return false;
}