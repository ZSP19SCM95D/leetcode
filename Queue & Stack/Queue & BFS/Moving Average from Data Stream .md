## Moving Average from Data Stream

### Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.

![image-20190726153329378](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726153329378.png)

~~~java
class MovingAverage {
    private int maxsize;
    private Queue<Integer> q;
    private double presum =0.0; 
    /** Initialize your data structure here. */
    public MovingAverage(int size) {
        q = new LinkedList<Integer>();
        maxsize =size;
    }
    
    public double next(int val) {
        if(q.size()==maxsize){
            presum -= q.remove();
        }
        
        presum+=val;
        q.add(val);
        return presum/q.size();  
    }
}

/**
 * Your MovingAverage object will be instantiated and called as such:
 * MovingAverage obj = new MovingAverage(size);
 * double param_1 = obj.next(val);
 */
~~~

### 本题考查queue的性质从后加从头删

