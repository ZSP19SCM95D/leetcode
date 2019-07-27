### Decode String

Given an encoded string, return its decoded string.

The encoding rule is: `k[encoded_string]`, where the *encoded_string* inside the square brackets is being repeated exactly *k* times. Note that *k* is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, *k*. For example, there won't be input like `3a` or `2[4]`.



**Examples:**

```
s = "3[a]2[bc]", return "aaabcbc".
s = "3[a2[c]]", return "accaccacc".
s = "2[abc]3[cd]ef", return "abcabccdcdcdef".
```

~~~java
class Solution {
    public String decodeString(String s) {
        Stack<Integer> num = new Stack<>();
        Stack<StringBuilder> str = new Stack<>();
        StringBuilder cur = new StringBuilder();
        int k = 0;
        
        for(char ch : s.toCharArray()){
            if (Character.isDigit(ch)) {
                k = k * 10 + ch - '0';
            } 
            else if ( ch == '[') {
                num.push(k);
                str.push(cur);
                cur = new StringBuilder();
                k = 0;
            } 
            else if (ch == ']') {
                StringBuilder tmp = cur;
                cur = str.pop();
                for (k = num.pop(); k > 0; --k) cur.append(tmp);
            } 
            else cur.append(ch);
        }
        return cur.toString();
        
    }
}
~~~

###我们这道题用两个 stack，一个用来保存个数，一个用来保存字符串如果遇到左括号，我们把当前计量数字k压入数字栈中，把当前字符串压入字符串栈中；如果遇到右括号时，我们取出数字栈中顶元素，存入变量k，然后给字符串栈的顶元素循环加上k个tmp字符串。
