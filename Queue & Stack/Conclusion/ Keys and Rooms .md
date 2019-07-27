### Keys and Rooms

There are `N` rooms and you start in room `0`.  Each room has a distinct number in `0, 1, 2, ..., N-1`, and each room may have some keys to access the next room. 

Formally, each room `i` has a list of keys `rooms[i]`, and each key `rooms[i][j]` is an integer in `[0, 1, ..., N-1]` where `N = rooms.length`.  A key `rooms[i][j] = v` opens the room with number `v`.

Initially, all the rooms start locked (except for room `0`). 

You can walk back and forth between rooms freely.

Return `true` if and only if you can enter every room.



**Example 1:**

```
Input: [[1],[2],[3],[]]
Output: true
Explanation:  
We start in room 0, and pick up key 1.
We then go to room 1, and pick up key 2.
We then go to room 2, and pick up key 3.
We then go to room 3.  Since we were able to go to every room, we return true.
```



~~~java
class Solution {
    HashSet<Integer> visited = new HashSet<>();
    public boolean canVisitAllRooms(List<List<Integer>> rooms) {
        
        enter(0,rooms);
        
        return  visited.size() == rooms.size();
        
    }
    
    public void enter(int roomnum, List<List<Integer>> rooms){
        visited.add(roomnum);
        List<Integer> keylist = rooms.get(roomnum);
        for(int key : keylist){
            if(!visited.contains(key)){
                enter(key,rooms);
            }
        }
        
    }
}
~~~

###这道题我用的递归的解法来做，用 HashSet 来记录访问过的房间，每次遍历此房间中的所有钥匙，如果有房间没有访问过，则调用递归。