# 题目
Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.\
分离出链表奇数和偶数节点。\
You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.
# 样例输出
Example:\
Given 1->2->3->4->5->NULL,\
return 1->3->5->2->4->NULL. 
# 分析
由于题目已经默认第一个为奇数节点，第二个为偶数节点，则可以设定odd（记录奇数节点）和even（记录偶数节点）两个链表，并初始化这两个链表使得分别指向表头和链表第二个节点，然后对head链表进行循环，依次把奇数和偶数节点加入两个链表中，并使得这两个链表错位相连，最后返回head即可。
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
    ListNode* oddEvenList(ListNode* head) {  
        if (head == NULL)  
       return NULL;
        if(head->next==NULL)
            return head;
        ListNode * odd = head;  
        ListNode * even = head->next;  
        ListNode * third = even;  
          while (even && even->next)  
        {  
            odd->next = even->next;  
            odd = odd->next;  
            even->next = odd->next;  
            even = even->next;  
        }  
          
        odd->next = third;  
        return head;  
    }  
};   
```
