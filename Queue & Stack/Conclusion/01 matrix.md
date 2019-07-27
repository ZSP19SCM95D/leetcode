### 01 Matrix

Given a matrix consists of 0 and 1, find the distance of the nearest 0 for each cell.

The distance between two adjacent cells is 1.

 

**Example 1:**

```
Input:
[[0,0,0],
 [0,1,0],
 [0,0,0]]

Output:
[[0,0,0],
 [0,1,0],
 [0,0,0]]
```

~~~java
class Solution {
    public int[][] updateMatrix(int[][] matrix) {
        int r = matrix.length;
        int l = matrix[0].length;
        
        Queue<int[]> q = new LinkedList<>();
        for(int i = 0;i<r;i++){
            for(int j = 0; j<l;j++){
                if(matrix[i][j] == 0){
                    q.offer(new int[] {i,j});
                }
                else{
                    matrix[i][j] = Integer.MAX_VALUE;
                }    
            }
        }
        
        int[][] dir = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
        
        while(!q.isEmpty()){
            int[] cell = q.poll();
            for (int[] d : dir) {
                int row = cell[0] + d[0];
                int col = cell[1] + d[1];
                if (row < 0 || row >= r || col < 0 || col >= l || 
                    matrix[row][col] <= matrix[cell[0]][cell[1]] + 1) continue;
                q.add(new int[] {row, col});
                matrix[row][col] = matrix[cell[0]][cell[1]] + 1;
            }
        }
        
        return  matrix;
    }
}
~~~

###BFS遍历: 从queue中取出一个为0的数字，遍历其周围四个点，如果越界或者周围点的值小于等于当前值加1，则return。如果大于则将周围点的值更新为当前值加1，然后继续BFS。