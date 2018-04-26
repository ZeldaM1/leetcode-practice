# 题目
Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.\
删除链表中重复元素
# 样例输出
Example 1:\
Input: 1->2->3->3->4->4->5\
Output: 1->2->5\
Example 2:\
Input: 1->1->1->2->3\
Output: 2->3
# 分析
本题可以构造一个第二个节点指向head表头的链表p来考虑从第一个节点就有重复元素的情况，然后从头指针开始读取数据，若有连续的节点val不相同则使得进入下一节点分析，否则使得当前节点的next指针指向连续节点的下一节点，由此遍历完链表取得的链表p即包含了不重复的元素和多余的一个节点，返回第二个节点即可。
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
    ListNode* deleteDuplicates(ListNode* head) {
               if(head==NULL || head->next==NULL)
            return head;
        ListNode *p=new ListNode(0);
        p->next=head;
        ListNode *q=p;
        ListNode *k=q->next;
                while(k->next){
            if(k->next->val!=k->val){
                if(q->next==k)
                    q=k;
                else
                    q->next=k->next;
            }
            k=k->next;
        }
                if(q->next!=k)
            q->next=k->next;
                return p->next;
    }
};
```