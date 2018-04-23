# 题目
Given a linked list, remove the n-th node from the end of list and return its head.
Note:
Given n will always be valid.
# 样例输出
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
Note:
Given n will always be valid.
# 分析
由于单向链表不能从末尾遍历回到表头，则可以先计算出链表长度然后算出正向遍历需要到达的位置，再使得当前位置的下一位指针指向当前位的下下位，返回链表头指针即可。
# 程序实现
```cpp
/ * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode*p=head;
         ListNode*p2=p->next;
        int m=0;
        while(p){
            p=p->next;
           m++;
        }
        int q=m-n;
        if(q==0)
        {
            p=head;  
            head=head->next;  
            delete p;  
            return head; 
        }
        int k=1;
        p=head;
        if(m==1)
            return p;
    while(k!=q){
        p=p->next; 
        k++;
    }
         p2=p->next;
        p->next=p2->next;
       p=head;
        return p;
    }
};
```
