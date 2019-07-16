### Given a **non-empty** array of digits representing a non-negative integer, plus one to the integer.

### The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.

### You may assume the integer does not contain any leading zero, except the number 0 itself.

#### Example

```
Input: [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

~~~java
class Solution {
    public int[] plusOne(int[] digits) {
        int n = digits.length;
        for(int i = n-1; i>=0; i--){
            if(digits[i]<9){
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }
        int[] newNumber = new int [n+1];
        newNumber[0] = 1;
    
        return newNumber;           
    }
}
~~~



#### 这是一个比较棘手的问题，看起来简单，其实有很多特殊情况，比如说999这个数字 当plus1 的时候 需要重新创建一个新数字， 长度比原数组长度多一位。再比如说899这个数字，我们需要从最后一位开始往前遍历，逐步将位数数字为九的改为零，直到不为九的位数加一。



