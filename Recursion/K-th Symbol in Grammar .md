### K-th Symbol in Grammar

On the first row, we write a `0`. Now in every subsequent row, we look at the previous row and replace each occurrence of `0` with `01`, and each occurrence of `1` with `10`.

Given row `N` and index `K`, return the `K`-th indexed symbol in row `N`. (The values of `K` are 1-indexed.) (1 indexed).

```
Examples:
Input: N = 1, K = 1
Output: 0

Input: N = 2, K = 1
Output: 0

Input: N = 2, K = 2
Output: 1

Input: N = 4, K = 5
Output: 1

Explanation:
row 1: 0
row 2: 01
row 3: 0110
row 4: 01101001
```



~~~java
class Solution {
    public int kthGrammar(int N, int K) {
        //当K是奇数的时候，我们就将其换成K+1，当K是偶数的时候，我们将其换为K/2。然后每次都对结果res（初始化为0）进行‘亦或’1操作，循环的终止条件是当K等于1时
        int res = 0;
        while (K > 1) {
            K = (K % 2 == 1) ? K + 1 : K / 2;
            res ^= 1;
        }
        return res;
        
    }
}

//binary tree 左节点右节点规律： 左节点（奇数）的父节点位置是（k+1）/2，数字与父节点相同；
//右节点（偶数）的父节点位置是k/2，数字与父节点相反
class Solution {
public:
    int kthGrammar(int N, int K) {
        if (N == 1) return 0;
        if (K % 2 == 0) return (kthGrammar(N - 1, K / 2) == 0) ? 1 : 0;
        else return (kthGrammar(N - 1, (K + 1) / 2) == 0) ? 0 : 1;
    }
}
~~~

### 注意观察规律 将其形象为binary tree

