# 题目
Write a program to find the node at which the intersection of two singly linked lists begins.\
If the two linked lists have no intersection at all, return null.\
The linked lists must retain their original structure after the function returns. \
You may assume there are no cycles anywhere in the entire linked structure.\
Your code should preferably run in O(n) time and use only O(1) memory.\
编写一个程序来查找两个单链表的交集开始的节点。
如果两个链表没有交集，则返回null。\
在函数返回后，链表必须保留原来的结构。\
您可以假设在整个链接结构中没有任何循环。
# 样例输出
For example, the following two linked lists: \
A:          a1 → a2->c1 → c2 → c3        
B:     b1 → b2 → b3->c1 → c2 → c3
# 分析
这道题其实就是在比较两个单项链表的节点是否相同，但须注意的是，在两个链表的交集节点之前链表的长度可能不同，故不能单纯的使当前节点指针指向下一节点，而需要使得长的链表先走distance步（distance为两个链表长度差值）
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
    int length(ListNode *p){
        int len=0;
        while(p){
            len++;
            p=p->next;
        }
        return len;
    }
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        int lenA=0,lenB=0;
        int distance;
        lenA=length(headA);
        lenB=length(headB);
      distance= lenA - lenB;     
           if(distance>0){
            for(int i=0;i<distance;i++)
            headA=headA->next;
        }
        else
        {
            for(int i=0;i<abs(distance);i++)
                 headB=headB->next;
        }
        while (headB!=NULL && headA!=NULL) {  
            if (headB == headA) {  
                return headA;  
            }  

            headB = headB->next;  
            headA = headA ->next;  
        }  
        return NULL;  
          
    } 
};
