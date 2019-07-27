## walls and gates

You are given a *m x n* 2D grid initialized with these three possible values.

1. `-1` - A wall or an obstacle.
2. `0` - A gate.
3. `INF` - Infinity means an empty room. We use the value `231 - 1 = 2147483647` to represent `INF` as you may assume that the distance to a gate is less than `2147483647`.

Fill each empty room with the distance to its *nearest* gate. If it is impossible to reach a gate, it should be filled with `INF`.

![image-20190726153735911](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726153735911.png)



~~~java
class Solution {
    public void wallsAndGates(int[][] rooms) {
        if(rooms.length == 0||rooms == null) return;
        Queue<int[]> q = new LinkedList<>();
        int inf = Integer.MAX_VALUE;
        int col = rooms.length;
        int row = rooms[0].length;
        for(int i = 0;i<col;i++){
            for(int j = 0; j<row;j++){
                if(rooms[i][j] ==0){
                    q.offer(new int[]{i,j});
                }
            }
        }
        
        while(!q.isEmpty()){
            int[] po = q.poll();
            int r = po[0], c = po[1];
            if(r>0&&rooms[r-1][c] == inf){
                rooms[r-1][c] = rooms[r][c]+1;
                q.offer(new int[]{r-1,c});
            }
            if(r<col-1&&rooms[r+1][c] == inf){
                rooms[r+1][c] = rooms[r][c]+1;
                q.offer(new int[]{r+1,c});
            }
            if(c>0&&rooms[r][c-1] == inf){
                rooms[r][c-1] = rooms[r][c]+1;
                q.offer(new int[]{r,c-1});
            }
            if(c<row-1&&rooms[r][c+1] == inf){
                rooms[r][c+1] = rooms[r][c]+1;
                q.offer(new int[]{r,c+1});
            }
        }
        
    }
}
~~~

### Solution

#### 这道题借助queue，我们首先把门的位置都排入queue中，然后开始循环，对于门位置的四个相邻点，我们判断其是否在矩阵范围内，并且位置值是否大于上一位置的值加1，如果满足这些条件，我们将当前位置赋为上一位置加1，并将次位置排入queue中，这样等queue中的元素遍历完了，所有位置的值就被正确地更新了

