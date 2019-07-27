### Flood Fill

An `image` is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate `(sr, sc)` representing the starting pixel (row and column) of the flood fill, and a pixel value `newColor`, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

**Example 1:**

```
Input: 
image = [[1,1,1],[1,1,0],[1,0,1]]
sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: 
From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected 
by a path of the same color as the starting pixel are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected
to the starting pixel.
```

~~~java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        if(image[sr][sc] == newColor) return image;
        fill(image,sr,sc,image[sr][sc],newColor);
        return image;
        
    }
    
    
    public void fill(int[][] image,int r, int c,int color,int newcolor){
        if(r<0 || r>=image.length || c<0 || c>=image[0].length||image[r][c] != color){
            return;
        }
        image[r][c] = newcolor;
        fill(image,r-1,c,color,newcolor);
        fill(image,r+1,c,color,newcolor);
        fill(image,r,c-1,color,newcolor);
        fill(image,r,c+1,color,newcolor);
    }
}
~~~

### Solution

### 这道题也是一道很经典的找相同区间的题目 用DFS比较简洁。在递归函数fill中，如果越界或者当前颜色跟起始颜色不同，直接返回。否则就给当前位置赋上新的颜色，然后对周围四个点继续调用递归函数。