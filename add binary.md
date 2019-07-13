### add binary

#### Given two binary strings, return their sum (also a binary string).

#### The input strings are both **non-empty** and contains only characters `1` or `0`.

#### ![image-20190712172042915](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190712172042915.png)



~~~java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder res = new StringBuilder();
        int i = a.length()-1;
        int j = b.length() -1;
        int jinwei = 0;
        
        while(i>=0 || j>=0){
            int sum = jinwei;
            if(i>=0) sum+=a.charAt(i--)-'0';
            if(j>=0) sum+=b.charAt(j--)-'0';
            res.append(sum%2);
            jinwei = sum/2;
        }
        if(jinwei!=0){res.append(jinwei);}
        return res.reverse().toString();
        
    }
}
~~~

### 从两个字符串的最后一位开始（已转化为stringbuilder）计算每一位的相加结果。注意当while循环结束后若还有进位则需另外附上一位。

#### when we have a char that represents a ASCII/unicode digit, and the smallest possible ASCII/unicode digit is substracted, then value corresponding to the digit would be left. Thus, here, when we get char from s1.charAt(first), subtract it from '0' can help us get the corresponding value to the digit. 

#### quoted from the comments



