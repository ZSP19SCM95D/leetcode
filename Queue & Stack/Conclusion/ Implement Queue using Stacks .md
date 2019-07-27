### Implement Queue using Stacks

Implement the following operations of a queue using stacks.

- push(x) -- Push element x to the back of queue.
- pop() -- Removes the element from in front of queue.
- peek() -- Get the front element.
- empty() -- Return whether the queue is empty.
- ![image-20190726181339217](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726181339217.png)



~~~java
 class MyQueue {
    
      Stack<Integer> s1 = new Stack();
        Stack<Integer> s2 = new Stack();
    
    /** Initialize your data structure here. */
    public MyQueue() {
      
        
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
           while (!s2.isEmpty())
        s1.push(s2.pop());
        s1.push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
        peek();
        return s2.pop();
    }
    
    /** Get the front element. */
    public int peek() {
        if(s2.isEmpty()){
            while(!s1.isEmpty()){
                
                s2.push(s1.pop());
                
            }
            
        }
        
        return s2.peek();
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        return  s1.isEmpty() && s2.isEmpty();
    }
}
~~~

