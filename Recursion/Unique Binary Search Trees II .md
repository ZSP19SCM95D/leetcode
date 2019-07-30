### Unique Binary Search Trees II

Given an integer *n*, generate all structurally unique **BST's** (binary search trees) that store values 1 ... *n*.

**Example:**

```
Input: 3
Output:
[
  [1,null,3,2],
  [3,2,null,1],
  [3,1,null,null,2],
  [2,1,3],
  [1,null,2,null,3]
]
Explanation:
The above output corresponds to the 5 unique BST's shown below:

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```

~~~java
class Solution {
    public List<TreeNode> generateTrees(int n) {
        if(n == 0){
            return new ArrayList<>();
        }
        return helper(1,n);
    }
    
    public List<TreeNode> helper(int low, int high){
        List<TreeNode> res = new ArrayList<>();
        if(low>high){
            res.add(null);
            return res;
        }
        for(int i = low; i<=high; i++){
            for(TreeNode left: helper(low,i-1)){
                for(TreeNode right: helper(i+1,high)){
                    TreeNode root = new TreeNode(i);
                    root.left = left;
                    root.right = right;
                    res.add(root);
                }
                
            }
        }
        return res;
        
    }
}
~~~

###这个题用到了分治法 Divide and Conquer，划分左右子树，递归构造。刚开始时，我们将区间 [1, n] 当作一个整体，然后我们需要将其中的每个数字都当作根结点，其划分开了左右两个子区间，然后分别调用递归函数。