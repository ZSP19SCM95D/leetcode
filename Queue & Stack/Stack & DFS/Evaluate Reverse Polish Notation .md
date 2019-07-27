### Evaluate Reverse Polish Notation

Evaluate the value of an arithmetic expression in [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Valid operators are `+`, `-`, `*`, `/`. Each operand may be an integer or another expression.

**Note:**

- Division between two integers should truncate toward zero.
- The given RPN expression is always valid. That means the expression would always evaluate to a result and there won't be any divide by zero operation.

![image-20190726174532818](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726174532818.png)


~~~java
class Solution {
    public int evalRPN(String[] tokens) {
        int a, b;
        Stack<Integer> st = new Stack<>();
        for(String s:tokens){
            if(s.equals("+")){
                st.add(st.pop()+st.pop());
            }
            else if(s.equals("-")){
                a= st.pop();
                b = st.pop();
                st.add(b-a);
            }
            else if (s.equals("*")){
                st.add(st.pop()*st.pop());
            }
            else if (s.equals("/")){
                a = st.pop();
                b = st.pop();
                st.add(b/a);
            }
            else{
                st.push(Integer.parseInt(s));
            }
        }
        return st.pop();
        
    }
}
~~~

