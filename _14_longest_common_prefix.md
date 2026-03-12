# longest common prefix

## Problem statement:
Longest Common Prefix
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
 

Constraints:

1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lowercase English letters if it is non-empty.

## Approach:
1. Handle Edge Case

If array is empty → return ""

2. Sort the Array

Sort strings in dictionary (lexicographical) order.

👉 Why?

After sorting,

First string = smallest

Last string = largest

These two will have the maximum difference.

If they share a prefix → all other strings will also share it.

3. Take First and Last String
String first = strs[0];
String last = strs[strs.length - 1];
4. Compare Characters

Start from index 0:

If characters match → move forward

If mismatch → stop

5 Return Common Part

Return substring from 0 to index.

## Code:
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {

        if(strs == null || strs.length == 0)
            return "";

        Arrays.sort(strs);

        String str1=strs[0];
        String str2=strs[strs.length-1];

        int index=0;

        while(index<str1.length() && index < str2.length()) {
            if(str1.charAt(index)==str2.charAt(index)) {
                index++;
            } else {
                break;
            }
        }
            return index==0?"" : str1.substring(0,index);  
    } 
}
```