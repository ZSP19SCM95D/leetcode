###In a given integer array nums, there is always exactly one largest element.

### Find whether the largest element in the array is at least twice as much as every other number in the array.

### If it is, return the **index** of the largest element, otherwise return -1.

~~~java
class Solution {
    public int dominantIndex(int[] nums) {
        if(nums.length==1){
            return 0;
        }
        //initialize the largest and second largest number index
        int l1=-1, l2=-1, index = -1;
        for(int i = 0;i <nums.length; i++){
            if(nums[i]>l1){
                l2 = l1;
                l1 = nums[i];
                index = i;
            }
            else if(nums[i]>l2){
                l2 =nums[i];
            } 
        }
        
        if(l1>=l2*2)
            return index;
        else
            return -1;
        
        
    }
}
~~~

#### 这道题比较简单，遍历一遍存好最大和第二大的数字，最后再比较最大的数字是否超过第二大的一倍。



