## Pascal's Triangle II

Given a non-negative index *k* where *k* ≤ 33, return the *k*th index row of the Pascal's triangle.

Note that the row index starts from 0.

![image-20190716175055249](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190716175055249.png)

~~~java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> rows = new ArrayList<Integer>();
        if(rowIndex<0){
            return rows;
        }
        for(int i =0; i<rowIndex+1; i++){
            rows.add(1);
            for(int j=i-1;j>0;j--){
                rows.set(j,rows.get(j-1)+rows.get(j));
            }
            
        }
        return rows;
        
    }
}
~~~



### 这道题是杨辉三角第一道题的简单版 少了一个list嵌套

