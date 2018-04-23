# 题目
Given a singly linked list L: L0→L1→…→Ln-1→Ln,
reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…
You may not modify the values in the list's nodes, only nodes itself may be changed.
# 样例输出
Example 1:
Given 1->2->3->4, reorder it to 1->4->2->3.
Example 2:
Given 1->2->3->4->5, reorder it to 1->5->2->4->3.
# 分析
可以先用一个链表1来保存head链表的第2位及以后的节点，另设一个链表2保存head链表最后的节点，然后使得head链表从头开始先指向尾部节点（链表2节点），然后再指向链表1节点。
# 程序实现
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    void reorderList(ListNode* head) {
    ListNode* p=head;
        ListNode* p1;
        ListNode* p3=head->next;
        while(p1)
        {
            p1=head->next;
            head=head->next;
            p1=p1->next;
            
        }
        ListNode* p2=head;
       head=p;
        head=head->next;
        head=p2;
        p1=p3;
        while(p1){
            head=head->next;
            head=p1;
            p1=p1->next;
        }
      
    }
};
```
