Given an array *nums* and a value *val*, remove all instances of that value [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

![image-20190715155735525](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190715155735525.png)



~~~java
class Solution {
    public int removeElement(int[] nums, int val) {
        int res = 0;
        for(int i = 0; i<nums.length; i++){
            if(nums[i]!=val){
                nums[res] = nums[i];
                res++;
            }
        }
        return res;
    }
}
~~~



