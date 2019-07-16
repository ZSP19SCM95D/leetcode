Given a binary array, find the maximum number of consecutive 1s in this array.

![image-20190715162618757](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190715162618757.png)

~~~java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int maxnow = 0, max = 0;
        for (int n : nums)
            maxnow = n == 0 ? 0 : maxnow + 1);
            max = Math.max(max, maxnow);
        return max; 
        
    }
}
~~~

### reset the maxnow to 0 when the nuns[i] equals to zero and compare to the max values we get before the reset

 