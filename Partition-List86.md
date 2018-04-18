# 题目
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.\
You should preserve the original relative order of the nodes in each of the two partitions.\
给定一个链表和一个值x，对链表分段，所有小于X的元素都排在大于等于X的前面。并保留两个分区中每个节点的原始相对顺序。
# 样例输出
For example,
Given 1->4->3->2->5->2 and x = 3,
return 1->2->2->4->3->5.
# 分析
1. 可以先对链表的第一个节点的val值进行讨论，（以大于x为例）设定一个p来遍历链表，设定small和big来分别记录小于和大于x的数，最后采用merge指令合并small和big链表。\
2. 可以通过创建两个新的头结点指针，来分别指向小于x的结点和大于等于x的结点，遍历结束之后，再将两个新的链表重新连接起来。
# 程序实现
* 1 merge用不了就很懵
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
    ListNode* partition(ListNode* head, int x) {
       ListNode *p=head->next;
        ListNode *q=head->next;
        
        if(head->val<x){
            ListNode* small=head;
            ListNode *big;
            while(p){
               while(p->val>x)
               {
                  big=p;
                   big=big->next;
                   p=p->next;
               }
                small->next=p;
                small=small->next;
                p=p->next;
                }
        small.merge(big);
        return small;
        }
    else if(head->val>x){
        ListNode* big=head;
        ListNode *small;
        while(p)
        {        
            while(p->val<x){
               small=p;
                   small=small->next;
                   p=p->next;
            }
             big->next=p;
                big=big->next;
                p=p->next;
        }
    small.merge(big);
        return small;
    }   
    }
};
```
* 2 AC的做法
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
    ListNode* partition(ListNode* head, int x) {
        ListNode *left_head=NULL,*left_tail=NULL;
        ListNode *right_head=NULL,*right_tail=NULL;
        ListNode *p=head;
        
        while(p){
            if(p->val<x){
                if(left_tail){
                    left_tail->next=p;
                    left_tail=left_tail->next;
                }
                else
                    left_head=left_tail=p;
            }
            else{
                if(right_tail){
                    right_tail->next=p;
                    right_tail=right_tail->next;
                }
                else
                    right_head=right_tail=p;
            }
            p=p->next;
        }
        
        if(right_tail)
            right_tail->next=NULL;
        if(left_tail)
            left_tail->next=right_head;
            
        return left_head?left_head:right_head;
    }
};
