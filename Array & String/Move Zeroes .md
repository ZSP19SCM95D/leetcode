## Move Zeroes

### Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

![image-20190716181321334](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190716181321334.png)

~~~java
class Solution {
    public void moveZeroes(int[] nums) {
        if(nums.length==0||nums== null){
            return;
        }
        int i = 0;
        for(int num : nums){
            if(num!=0){
                nums[i++]=num;
            }
        }
        while(i<nums.length){
            nums[i++]=0;
        }
    }
}
~~~

### 学会灵活运用pointer

