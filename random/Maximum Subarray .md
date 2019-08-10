### Maximum Subarray

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

**Example:**

```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```



~~~java
class Solution {
    public int maxSubArray(int[] nums) {
        int res = Integer.MIN_VALUE, templarge =0;
        for(int i =0; i<nums.length; i++){
            templarge = Math.max(templarge+nums[i],nums[i]);
            res = Math.max(res,templarge);
        }
        return res;
        
    }
}
~~~



###和股票题目类似，设置全局最大和局部最大变量，遍历array，比较当前元素和之前相加和加上此元素，替换局部最大变量。然后再与最终结果比较。