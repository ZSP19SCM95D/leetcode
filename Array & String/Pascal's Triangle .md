a### Pascal's Triangle 杨辉三角

#### Given a non-negative integer *numRows*, generate the first *numRows* of Pascal's triangle.

![image-20190711223837785](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190711223837785.png)

~~~java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
      //base case
        if(numRows<=0){
            return res;
        }
        for(int i = 0; i<numRows;i++){
            List<Integer> rows = new ArrayList<Integer>();
          //careful about the boundaries i+1 because i is circling from 0
            for(int j= 0;j <i+1;j++){
                if(j==0 || j==i){
                    rows.add(1);
                }
                else{
                    rows.add(res.get(i-1).get(j-1)+res.get(i-1).get(j));
                }
            }
            res.add(rows);
        }
        return res;
        
    }
}
~~~

### 关键记录上一层的结点，每一层的第i个位置，等于上一层第i-1与第i个位置之和。然后注意打印顺序以及list嵌套list的存储

