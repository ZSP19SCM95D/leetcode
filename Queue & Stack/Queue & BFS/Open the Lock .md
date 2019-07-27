### Open the Lock

You have a lock in front of you with 4 circular wheels. Each wheel has 10 slots: `'0', '1', '2', '3', '4', '5', '6', '7', '8', '9'`. The wheels can rotate freely and wrap around: for example we can turn `'9'` to be `'0'`, or `'0'` to be `'9'`. Each move consists of turning one wheel one slot.

The lock initially starts at `'0000'`, a string representing the state of the 4 wheels.

You are given a list of `deadends` dead ends, meaning if the lock displays any of these codes, the wheels of the lock will stop turning and you will be unable to open it.

Given a `target` representing the value of the wheels that will unlock the lock, return the minimum total number of turns required to open the lock, or -1 if it is impossible.

![image-20190726155503292](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190726155503292.png)

~~~java
class Solution {
    public int openLock(String[] deadends, String target) {
        Set<String> begin = new HashSet<>();
        Set<String> end = new HashSet<>();
        Set<String> deads = new HashSet<>(Arrays.asList(deadends));
        begin.add("0000");
        end.add(target);
        int level = 0;
        while(!begin.isEmpty() && !end.isEmpty()) {
            Set<String> temp = new HashSet<>();
            for(String s : begin) {
                if(end.contains(s)) return level;
                if(deads.contains(s)) continue;
                deads.add(s);
                StringBuilder sb = new StringBuilder(s);
                for(int i = 0; i < 4; i ++) {
                    char c = sb.charAt(i);
                    String s1 = sb.substring(0, i) + (c == '9' ? 0 : c - '0' + 1) + sb.substring(i + 1);
                    String s2 = sb.substring(0, i) + (c == '0' ? 9 : c - '0' - 1) + sb.substring(i + 1);
                    if(!deads.contains(s1))
                        temp.add(s1);
                    if(!deads.contains(s2))
                        temp.add(s2);
                }
            }
            level ++;
            begin = end;
            end = temp;
        }
        return -1;
    }
}
~~~



### Solution:

#### 这道题其实本质就是个迷宫遍历的问题，只不过相邻位置不再是上下左右四个位置，而是四位数字每个都加一减一，总共有八个相邻的位置。遍历迷宫问题中求最短路径要用BFS来做,和经典BFS遍历迷宫解法唯一不同的就是找下一个位置的地方，这里我们要遍历四位数字的每一位，然后分别加1减1，这里我们采用拼接法来生成新字符串，而不是像上面那样使用置换字符串的方法。我们对于加一和减一分别进行拼接，注意处理9加1变0，和0减1变9的情况。

