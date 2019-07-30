### Fibonacci Number

The **Fibonacci numbers**, commonly denoted `F(n)` form a sequence, called the **Fibonacci sequence**, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,

```
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), for N > 1.
```

Given `N`, calculate `F(N)`.

 

**Example 1:**

```
Input: 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
```



~~~java
class Solution {
    HashMap<Integer,Integer> m = new HashMap<>();
    public int fib(int N) {
        if(m.containsKey(N)){
            return m.get(N);
        }
        int res;
        if(N<2){
            return N;
        }
        else{
            res = fib(N-1)+fib(N-2);
        }
        m.put(N,res);
        return res;
        
    }
}
~~~



### 记住用memoization避免overflow减少时间复杂度

### 这里使用哈希表避免重复计算



