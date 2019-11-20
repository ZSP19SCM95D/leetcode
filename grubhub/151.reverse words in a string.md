## Reverse Words in a String

Given an input string, reverse the string word by word.

 ![image-20190716175321381](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190716175321381.png)

~~~java
class Solution {
    public String reverseWords(String s) {
        if(s == null) return null;
        char[] a = s.toCharArray();
        int l = a.length;
        
        reverse(a,0,l-1);
        reverseword(a,l);
        return cleanspace(a,l);
        
        
    }
    
    public void reverse(char[] a, int start, int end){
        while(start<end){
            char t = a[start];
            a[start] = a[end];
            a[end] = t;
            start++;
            end--;
        }
    }
    
    public void reverseword(char[] a,int l){
        int i =0, j= 0;
        while (i < l) {
            while (i < j || i < l && a[i] == ' ') i++; // skip spaces
            while (j < i || j < l && a[j] != ' ') j++; // skip non spaces
            reverse(a, i, j - 1);                      // reverse the word
        }
    }
    
    public String cleanspace(char[] a,int l){
        int i = 0, j = 0;
      
        while (j < l) {
            while (j < l && a[j] == ' ') j++;             // skip spaces
            while (j < l && a[j] != ' ') a[i++] = a[j++]; // keep non spaces
            while (j < l && a[j] == ' ') j++;             // skip spaces
            if (j < l) a[i++] = ' ';                      // keep only one space
        }
  
        return new String(a).substring(0, i);
        
    }
}
~~~

###3 step:

```
// step 1. reverse the whole string
    reverse(a, 0, n - 1);
    // step 2. reverse each word
    reverseWords(a, n);
    // step 3. clean up spaces
    return cleanSpaces(a, n);
```

