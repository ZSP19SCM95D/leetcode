### Pow(x, n)

Implement [pow(*x*, *n*)](http://www.cplusplus.com/reference/valarray/pow/), which calculates *x* raised to the power *n* (xn).

**Example 1:**

```
Input: 2.00000, 10
Output: 1024.00000
```

**Example 2:**

```
Input: 2.10000, 3
Output: 9.26100
```



~~~java
class Solution {
    public double myPow(double x, int n) {
        if(n == 0){
            return 1;
        }
        if(n < 0){
            if( n == Integer.MIN_VALUE ) {
                //If n is Integer.MIN_VALUE, the code will have overflow runtime error.
                ++n;
                n = -n;
                x = 1/x;
                return x * x * myPow( x * x, n / 2 );
                }
            n = -n;
            x = 1/x;
        }
        return n%2==0 ? myPow(x*x, n/2) : x*myPow(x*x, n/2);
        
    }
}
~~~

### 这里用递归来折半计算，每次把n缩小一半。如果n是偶数，直接把上次递归得到的值算个平方返回即可，如果是奇数，则还需要乘上个x的值。这里test case中加了个负最小数后，就报错了。因为

```
Integer.MAX_VALUE =  ``2147483647
Integer.MIN_VALUE = -``2147483648
```

### 当负数绝对值取正时，会溢出。所以得再加一段代码。

