###  Spiral Matrix 螺旋矩阵


#### Given a matrix of *m* x *n* elements (*m* rows, *n* columns), return all elements of the matrix in spiral order

![image-20190711223351576](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190711223351576.png)

~~~java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> l = new ArrayList<>();
        if(matrix.length == 0) return l;
        int m = matrix.length, n = matrix[0].length;
        int up = 0,  down = m - 1,left = 0, right = n - 1;
        while (l.size() < n * m) {
            for (int j = left; j <= right && l.size() < n * m; j++)
                l.add(matrix[up][j]);
            
            for (int i = up + 1; i <= down - 1 && l.size() < n * m; i++)
                l.add(matrix[i][right]);
                     
            for (int j = right; j >= left && l.size() < n * m; j--)
                l.add(matrix[down][j]);
                        
            for (int i = down - 1; i >= up + 1 && l.size() < n * m; i--) 
                l.add(matrix[i][left]);
                
            left++; right--; up++; down--; 
        }
        return l;
         
    }
}
~~~

#### 这道题思路比较简单，就是用变量left, right, top, bottom记录左，右，顶，底。然后按照左到右，顶到底，右到左，底到顶的顺序循环，把遍历的元素加入到结果。

#### Time complexity of the above solution is O(mn).

