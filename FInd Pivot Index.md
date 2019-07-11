## Find Pivot index

####Given an array of integers `nums`, write a method that returns the "pivot" index of this array.

####We define the pivot index as the index where the sum of the numbers to the left of the index is equal to the sum of the numbers to the right of the index.

####If no such index exists, we should return -1. If there are multiple pivot indexes, you should return the left-most pivot index.



```java
class Solution {
    public int pivotIndex(int[] nums) {
        int index;
        double sum =0, temp =0;
        for(int i = 0; i<nums.length; i++){
            sum += nums[i];
        }    
				for(index =0;index<nums.length; index++){
        	if((sum-nums[index])/2==temp) return index;
        	temp +=nums[index];
    		}
    
    return -1;
    
}
}
```

#### 主要思路是先遍历一遍array 计算出总和， 第二次遍历array的时候用一个temp变量记录index走过的所有数的总和，比较它是否等于除去index指向数之外的另一半未遍历的数。# leetcode
