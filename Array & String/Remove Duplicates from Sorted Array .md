## Remove Duplicates from Sorted Array

### Given a sorted array *nums*, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appear only *once* and return the new length.Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

![image-20190716180745527](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190716180745527.png)



~~~java
class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums == null || nums.length == 0){
            return 0;
        }
        int i = 1;
        for(int j =1;j<nums.length;j++){
            if(nums[j]!= nums[j-1]){
                nums[i++] = nums[j];
            }
        }
        return i;
    }
}
~~~

