## Reverse Words in a String III

Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

![image-20190716180632066](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190716180632066.png)

~~~java
class Solution {
    public String reverseWords(String s) {
        char[] a = s.toCharArray();
        int n = a.length;
        int i=0,j=0;
        while(i<n){
            while(i<j||i<n&&a[i]==' ') i++;
            while(j<i||j<n&&a[j]!=' ') j++;
            reverse(a,i,j-1);
        }
        return new String(a);
    }
        
    public void reverse(char[] a,int i,int j){  
        while(i<j){
            char t = a[i];
            a[i] = a[j];
            a[j] = t;
            i++;
            j--;
        }
    }
    
}
~~~



### easy version of the Reverse Words in a String

