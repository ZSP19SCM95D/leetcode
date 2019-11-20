### 819. Most Common Word

Given a paragraph and a list of banned words, return the most frequent word that is not in the list of banned words.  It is guaranteed there is at least one word that isn't banned, and that the answer is unique.

Words in the list of banned words are given in lowercase, and free of punctuation.  Words in the paragraph are not case sensitive.  The answer is in lowercase.

**Example:**

```java
Input: 
paragraph = "Bob hit a ball, the hit BALL flew far after it was hit."
banned = ["hit"]
Output: "ball"
Explanation: 
"hit" occurs 3 times, but it is a banned word.
"ball" occurs twice (and no other word does), so it is the most frequent non-banned word in the paragraph. 
Note that words in the paragraph are not case sensitive,
that punctuation is ignored (even if adjacent to words, such as "ball,"), 
and that "hit" isn't the answer even though it occurs more because it is banned.
```

~~~java
class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
      HashMap<String,Integer> m = new HashMap<>();
      HashSet<String> set = new HashSet<>();
      
      for(String s : banned){
        set.add(s);
      }
      
      int max =0;
      String ans = "";
      
      StringBuilder sb = new StringBuilder();
      for(char c: paragraph.toCharArray()){
        if(Character.isLetter(c)){
          sb.append(Character.toLowerCase(c));
        }
        else if (sb.length()>0){
          String w = sb.toString();
          if(!banset.contains(w)){
            m.put(w,m.getOrDefault(w,0)+1);
            if(m.get(w)>max){
              ans = w;
              max = m.get(w);
            }
          }
          sb = new StringBuilder();
          
        }
      }
      return ans;
    }
}
~~~

### 这道题先用hashset存好所有被禁止的词语，将max赋值为0，然后开始遍历字符串para，创立stringbuilder将遍历到的字母一个个接入stringbuilder，当便利到非字母时，当作一个词语的结束，如果string长度大于零 则判断是否存在与hashmap中，存在则将对应value值加一，没有则将value值赋值为1，如果所对应value大于max，则更新max并将string值赋给结果。每次处理完一个word后更新stringbuilder。

