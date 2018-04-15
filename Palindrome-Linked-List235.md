# 题目
Given a singly linked list, determine if it is a palindrome.\
给定一个单向的链表，确定它是否是一个回文链表。
# 分析
链表中的数据形似12321的则为回文链表，那么可以先将链表中的数据用数组保存起来然后对数组进行遍历，
以12321为例，若从3的位置往后有数字是在3前面的对应位置不同的，则返回false，若遍历数组完成则可以返回true。
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
    bool isPalindrome(ListNode* head) {
        vector<int>v;
        while (head!=NULL)
        {
            v.push_back(head->val);
            head = head->next;
        }
        for (int i = 0; i < v.size() / 2;i++)
        {
            if (v[i] != v[v.size() - i - 1])
                return false;
        }
        return true;
    }
};
