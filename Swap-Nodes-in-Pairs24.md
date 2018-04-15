# 题目
Given a linked list, swap every two adjacent nodes and return its head.\
Note:\
Your algorithm should use only constant extra space.\
You may not modify the values in the list's nodes, only nodes itself may be changed.\
给定一个链表，交换每两个相邻的节点并返回它的头。
注意:\
不能修改列表节点中的值，只有节点本身可以更改。
# 样例输出
Example:\
Given 1->2->3->4, you should return the list as 2->1->4->3.
# 分析
题目要求更改节点本身以达到两两交换的目的，故可考虑遍历链表中的节点，使得每一个节点中的next指针都与下一节点中的指针进行交换即可。
ps：需要考虑到特殊情况，即链表中没有节点或只有一个节点。这样的话相应的返回false或者第一个节点。
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
        if(head == NULL) 
        return NULL;
        if(head->next == NULL) 
        return head;
        ListNode* temp = head->next;
        head->next = swapPairs(temp->next);
        temp->next = head;
        return temp;
    }
};
