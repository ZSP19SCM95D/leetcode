## Longest Common Prefix

### Write a function to find the longest common prefix string amongst an array of strings.If there is no common prefix, return an empty string “”

![image-20190713152306874](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190713152306874.png)

~~~java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length == 0){
            return "";
        }
        String pre = strs[0];
        for (int i = 1; i < strs.length; i++)
            while(strs[i].indexOf(pre) != 0)
                pre = pre.substring(0,pre.length()-1);
        return pre;
        
        
    }
}
~~~

###The idea of this algorithm is:

1. first assume the first word is the `prefix`, and then we will check whether `prefix` is all other word's prefix.

2. if `strs[i].indexOf(prefix) != 0` means it is not start with `prefix`. So we should cut down the prefix a little bit (remove the last character), that is: `prefix = prefix.substring(0, prefix.length() - 1);`

3. we continuously do this, util all the words checked, or the prefix has been cutted to `''` (that is why it is called `Horizontal scanning`)

   quoted from stackoverflow