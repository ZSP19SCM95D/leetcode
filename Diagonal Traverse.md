### diagonal traverse

####Given a matrix of M x N elements (M rows, N columns), return all elements of the matrix in diagonal order as shown in the below image.

 #### example

![](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190711170736399.png)

```java
class Solution {
    public int[] findDiagonalOrder(int[][] matrix) {
        if (matrix.length == 0)
            return new int[0];
        int r = 0, c = 0, m = matrix.length, n = matrix[0].length, arr[] = new int[m * n];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = matrix[r][c];
            //if r+c is oven, we can see from the graph the direction is pointing up;
            if((r+c)%2==0){
                //three case;
                if(r == 0) {c++;}
                else if (c == n-1) {r++;}
                else {r--;c++;}
            }
            //if r+c is odd, we can see from the graph the direction is pointing down;
            else{
                if(r == m - 1) { c++; }
                else if (c == 0) { r++; }
                else  { r++; c--; }
            }
        
        }
        return arr;
        
    }
}
```

#### Solution

#### 这道题主要在于找出走向图中规律 注意箭头在什么临界点发生转变

####Time complexity: O(m * n), m = number of rows, n = number of columns.
### #Space complexity: O(1).



