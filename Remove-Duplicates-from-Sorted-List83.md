# 题目
Given a sorted linked list, delete all duplicates such that each element appear only once.\
删除链表中重复元素。
# 样例输出
For example,\
Given 1->1->2, return 1->2.\
Given 1->1->2->3->3, return 1->2->3.
# 分析
可以设定两个位置相邻的指针p，q，分别代表链表中相邻位置的元素，对两个元素进行比较，\
若相同则使得p的下一节点指向p原有节点的下下节点，不同则使p当前位置和q相同，然后使p指向下一节点，由此遍历完链表中的所有节点所取得的head即为已删除重复元素的链表。
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
    ListNode *deleteDuplicates(ListNode *head) {  
        if(head==NULL)  
            return head;  
        ListNode* p=head;  
        ListNode* q=head->next;  
        while(q){  
            if(q->val==p->val) 
                p->next = q->next;  
            else
                p=q;  
            q = q->next;  
        }  
        return head;  
    }  
};
