### Number of Islands

#### Given a 2d grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

![image-20190726154857090](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726154857090.png)

~~~java
class Solution {
    public int numIslands(char[][] grid) {
        int count = 0;
        int col = grid.length;
        if(col==0) return 0;
        int row = grid[0].length;
        for(int i =0; i<col; i++){
            for(int j=0; j<row; j++){
                if(grid[i][j]=='1'){
                    DFS(grid,i,j,col,row);
                    count++;
                }
            }
        }
        return count;
        
    }
    
    public void DFS(char[][] grid, int i, int j,int col,int row){
        if(i<0||j<0||i>=col||j>=row||grid[i][j]!='1') return;
        grid[i][j] = '0';
        DFS(grid,i+1,j,col,row);
        DFS(grid,i-1,j,col,row);
        DFS(grid,i,j+1,col,row);
        DFS(grid,i,j-1,col,row);
    }
}
~~~



#### 这道求岛屿数量的题的本质是求矩阵中连续区域的个数，很容易想到需要用深度优先搜索 DFS 来解，对于一个为 ‘1’ 且未被访问过的位置，我们递归进入其上下左右位置上为 ‘1’ 的数，并将其赋为 0，继续进入其所有相连的邻位置，这样可以避免重复访问直到所有相邻的1全被赋值为零后，我们再找到下一个1的位置并count++。以此类推直至遍历完整个原数组即可得到最终结果。

