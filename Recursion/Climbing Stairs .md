### Climbing Stairs

You are climbing a stair case. It takes *n* steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Note:** Given *n* will be a positive integer.

**Example 1:**

```
Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```



~~~java
class Solution {
    HashMap<Integer,Integer> m = new HashMap<>();
    public int climbStairs(int n) {
        if(m.containsKey(n)){
            return m.get(n);
        }
        int res;
        if(n<=2){
            return n;
        }
        else{
            res = climbStairs(n-1)+climbStairs(n-2);
        }
        m.put(n,res);
        return res;
           
    }
}
~~~



### 跟上一道斐波那契数列题目很类似 注意观察归类

