# Min stack

## Problem statement:
155. Min Stack
Solved
Medium
Topics
premium lock icon
Companies
Hint
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the MinStack class:

MinStack() initializes the stack object.
void push(int val) pushes the element val onto the stack.
void pop() removes the element on the top of the stack.
int top() gets the top element of the stack.
int getMin() retrieves the minimum element in the stack.
You must implement a solution with O(1) time complexity for each function.

 

Example 1:

Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]

Explanation
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2
 

Constraints:

-231 <= val <= 231 - 1
Methods pop, top and getMin operations will always be called on non-empty stacks.
At most 3 * 104 calls will be made to push, pop, top, and getMin.

## Approach:



# Code
class MinStack {
 LinkedList<Integer> stk; //=newLinkedList<>();
 LinkedList<Integer> minstk;



    public MinStack() {
        stk = new LinkedList<>();
        minstk = new LinkedList<>();
    }
    
    public void push(int val) {
        stk.addLast(val);
        if(minstk.size() == 0) {
            minstk.addLast(val);
        }
        else{
            int a = val;
            int b = minstk.peekLast();
            int min = Math.min(a,b);
            minstk.addLast(min);
        }
        
    }
    
    public void pop() {
        stk.removeLast();
        minstk.removeLast();
        
    }
    
    public int top() {
        return stk.peekLast();
        
    }
    
    public int getMin() {
        return minstk.peekLast();
        
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */