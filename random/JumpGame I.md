\55. Jump Game

Medium

3216287Share

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

**Example 1:**

```java
Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Example 2:**



```java
Input: [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.
  
```

## my solu（Greedy）

~~~java

class Solution {
    public boolean canJump(int[] nums) {
        if(nums==null ||nums.length == 0) return false;
        int last = nums.length-1;
        for(int i =nums.length-1;i>=0;i--){
            if(i+nums[i]>=last){
                last = i;
            }
            
        }
        return last ==0;
        
    }
}
~~~

### Bruce Force

#### 从startpoint开始尝试所以距离的jump 看是否能到达lastpoint

### 优化解

#### Dynamic Programming Top-down

1. Initially, all elements of the `memo` table are *UNKNOWN*, except for the last one, which is (trivially) *GOOD* (it can reach itself)

2. Modify the backtracking algorithm such that the recursive step first checks if the index is known (

   GOOD

   BAD

   )

   1. If it is known then return *True* / *False*
   2. Otherwise perform the backtracking steps as before

3. Once we determine the value of the current index, we store it in the `memo` table

~~~java
enum Index {
    GOOD, BAD, UNKNOWN
}//An enum type is a special data type that enables for a variable to be a set of predefined constants. The variable must be equal to one of the values that have been predefined for it. Common examples include compass directions (values of NORTH, SOUTH, EAST, and WEST) and the days of the week.

public class Solution {
    Index[] memo;

    public boolean canJumpFromPosition(int position, int[] nums) {
        if (memo[position] != Index.UNKNOWN) {
            return memo[position] == Index.GOOD ? true : false;
        }

        int furthestJump = Math.min(position + nums[position], nums.length - 1);
        for (int nextPosition = position + 1; nextPosition <= furthestJump; nextPosition++) {
            if (canJumpFromPosition(nextPosition, nums)) {
                memo[position] = Index.GOOD;
                return true;
            }
        }

        memo[position] = Index.BAD;
        return false;
    }

    public boolean canJump(int[] nums) {
        memo = new Index[nums.length];
        for (int i = 0; i < memo.length; i++) {
            memo[i] = Index.UNKNOWN;
        }
        memo[memo.length - 1] = Index.GOOD;
        return canJumpFromPosition(0, nums);
    }
}
~~~

### Dynamic Programming Bottom-up

Top-down to bottom-up conversion is done by eliminating recursion. In practice, this achieves better performance as we no longer have the method stack overhead and might even benefit from some caching. More importantly, this step opens up possibilities for future optimization. The recursion is usually eliminated by trying to reverse the order of the steps from the top-down approach.

The observation to make here is that we only ever jump to the right. This means that if we start from the right of the array, every time we will query a position to our right, that position has already be determined as being *GOOD* or *BAD*. This means we don't need to recurse anymore, as we will always hit the `memo` table.

~~~java
enum Index {
    GOOD, BAD, UNKNOWN
}

public class Solution {
    public boolean canJump(int[] nums) {
        Index[] memo = new Index[nums.length];
        for (int i = 0; i < memo.length; i++) {
            memo[i] = Index.UNKNOWN;
        }
        memo[memo.length - 1] = Index.GOOD;

        for (int i = nums.length - 2; i >= 0; i--) {
            int furthestJump = Math.min(i + nums[i], nums.length - 1);
            for (int j = i + 1; j <= furthestJump; j++) {
                if (memo[j] == Index.GOOD) {
                    memo[i] = Index.GOOD;
                    break;
                }
            }
        }

        return memo[0] == Index.GOOD;
    }
}
~~~

