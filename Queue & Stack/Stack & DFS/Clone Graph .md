### Clone Graph

Given a reference of a node in a **connected** undirected graph, return a [**deep copy**](https://en.wikipedia.org/wiki/Object_copying#Deep_copy) (clone) of the graph. Each node in the graph contains a val (`int`) and a list (`List[Node]`) of its neighbors.

 ![image-20190726174736725](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726174736725.png)

~~~java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;

    public Node() {}

    public Node(int _val,List<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/
class Solution {
    public HashMap<Integer,Node> m = new HashMap<>();
    public Node cloneGraph(Node node) {
        return clone(node);
        
    }
    
    public Node clone(Node node){
        if(node == null) return null;
        if(m.containsKey(node.val)){
            return m.get(node.val);
        }
        
        Node newnode = new Node(node.val,new ArrayList<Node>());
        m.put(newnode.val,newnode);
        for(Node neighbor: node.neighbors)
            newnode.neighbors.add(clone(neighbor));
        return newnode;
    }
}
~~~

###这道问题和之前的 Copy List with Random Pointer 有些类似，这道题我们用HashMap 来对应原图中的结点和新生成的克隆图中的结点