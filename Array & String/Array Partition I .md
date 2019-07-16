Array Partition I

Given an array of **2n** integers, your task is to group these integers into **n** pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

![image-20190715145929897](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190715145929897.png)

~~~java
class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
        int res=0;
        for(int i =0;i<nums.length;i+=2){
            res +=nums[i];
        }
        return res;
        
        
    }
}
~~~

