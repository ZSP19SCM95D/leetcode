Given an array of integers that is already **sorted in ascending order**, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

**Note:**

- Your returned answers (both index1 and index2) are not zero-based.
- You may assume that each input would have *exactly* one solution and you may not use the *same* element twice.

![image-20190715150128513](/Users/zhongzhuding/Desktop/image-20190715150128513.png)

~~~java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        HashMap<Integer,Integer> s = new HashMap<>();
        int[] res = new int[2];
        for(int i = 0; i<numbers.length;i++){
            if(s.containsKey(target-numbers[i])){
                res[0] = s.get(target-numbers[i])+1;
                res[1] = i+1;
                return res;   
            }
            else
                s.put(numbers[i],i);
        }
        return res;
    }
}
~~~



### 这道题主要思路采用hashmap存储对应的nums 和对应的index组成map

