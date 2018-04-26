# 题目
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time. \
设计一个栈使得其支持以下操作。\
push(x) -- Push element x onto stack.\ 
pop() -- Removes the element on top of the stack.\ 
top() -- Get the top element. \
getMin() -- Retrieve the minimum
element in the stack. 
# 样例输出
Example:\
MinStack minStack = new MinStack();\
minStack.push(-2);\
minStack.push(0);\
minStack.push(-3);\
minStack.getMin();   --> Returns -3.\
minStack.pop();\
minStack.top();      --> Returns 0.\
minStack.getMin();   --> Returns -2.
# 分析
这道题实际上就只需要在栈的基础上写出一个能找到最小值操作的步骤，则可以在对象的内部使用两个栈，一个拿来存储数据，另一个拿来存最小的值即可。
# 程序实现
```cpp
class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() {}  
    void push(int x) {
        stack1.push(x);
        if(stack2.empty()||stack2.top()>x)
            stack2.push(x);
    }
    
    void pop() {
         if(stack1.top()==stack2.top())
             stack2.pop();
        stack1.pop();
    }
    
    int top() {
        return stack1.top();
       
    }
    
    int getMin() {
        return stack2.top();
    }
    private:
    stack<int>stack1;
     stack<int>stack2;
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
 ```
 2ms也超时。。（黑脸黑脸 > _ <）