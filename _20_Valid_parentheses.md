# Valid parentheses
 
## problem statement:
20. Valid Parentheses
Solved
Easy
Topics
premium lock icon
Companies
Hint
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 

Example 1:

Input: s = "()"

Output: true

Example 2:

Input: s = "()[]{}"

Output: true

Example 3:

Input: s = "(]"

Output: false

Example 4:

Input: s = "([])"

Output: true

Example 5:

Input: s = "([)]"

Output: false

 

Constraints:

1 <= s.length <= 104
s consists of parentheses only '()[]{}'.

## Approach:



## Code:
class Solution {
    public boolean isValid(String s) {
        LinkedList<Character> stack = new LinkedList<>();
        for(char ch : s.toCharArray()) {
            if(ch == '(' || ch == '{' || ch == '[') {
                stack.addLast(ch);
            }
            else {
                if(stack.isEmpty()) {
                    return false;
                }
                else if(
                    (ch == ')' && stack.peekLast() == '(') ||
                    (ch == ']' && stack.peekLast() == '[') ||
                    (ch == '}' && stack.peekLast() == '{') 
                ) {
                    stack.removeLast();
                }
                else {
                    return false;
                }
            }
        }
        return stack.isEmpty();
    }
}