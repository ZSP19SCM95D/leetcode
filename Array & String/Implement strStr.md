### Implement strStr

### Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

![image-20190713143955112](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190713143955112.png)

~~~java
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle.isEmpty()){
            return 0;
        }
        for (int i = 0; i <= haystack.length() - needle.length(); i++) {
            for (int j = 0; j < needle.length() && haystack.charAt(i + j) == needle.charAt(j); j++)
                if (j == needle.length() - 1) return i;
        }
        return -1;
        
        
    }
}
~~~



### 这题注意两次循环边界即可

