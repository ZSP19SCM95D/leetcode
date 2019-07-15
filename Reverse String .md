Reverse String

Write a function that reverses a string. The input string is given as an array of characters `char[]`.

Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

You may assume all the characters consist of [printable ascii characters](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

~~~java
class Solution {
    public void reverseString(char[] s) {
        int i = 0;
        int j = s.length-1;
        while(i<j){
            swap(s,i,j);
            i++;
            j--;
        }
    }
    
    public void swap(char[]s,int i,int j){
        char temp;
        temp = s[i];
        s[i] = s[j];
        s[j] = temp;
    }
}
~~~

