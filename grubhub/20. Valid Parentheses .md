### Valid Parentheses

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. ![image-20190726164552082](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726164552082.png)

~~~java
class Solution {
    public boolean isValid(String s) {
        
        Stack<Character> st = new Stack<Character>();
        
        for(char a : s.toCharArray()){
            if(a =='('){
                st.push(')');
            }
            else if(a == '{'){
                st.push('}');
            }
            else if(a == '['){
                st.push(']');
            }
            else if (st.isEmpty() || st.pop() != a){
                return false;
            }
        }
        return st.isEmpty();
        
    }
}
~~~

