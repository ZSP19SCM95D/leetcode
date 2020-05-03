```java
class Solution {
   public HashMap<String, List<String>> favoriteVideoGenre(Map<String, List<String>> userMap, Map<String, List<String>> genreMap) {
   	Map<String, List<String>> res = new HashMap<>();
   	Map<String, String> bookstogenre = new HashMap<>();
   	
   	for(String genre : genreMap.keySet()) {
   		List<String> books = genreMap.get(genre);
   		for(String book : books) {
   			bookstogenre.put(book, genre);
   		}
   	}
       Map<String, Integer> count = new HashMap();
   	int max = 0;
   	for(String user : userMap.keySet()) {
            count = new HashMap();
            max = 0;
            res.put(user, new ArrayList());
            List<String> books = userMap.get(user);
            for(String book : books) {
                if (!bookstogenre.containsKey(book)) continue;
                String genre = bookstogenre.get(book);
                int c = count.getOrDefault(genre, 0) + 1;
                count.put(genre, c);
                max = Math.max(c, max);
                      }
            for (String key : count.keySet()) {
                if (count.get(key) == max) {
                         res.get(user).add(key);
                     }
                 }
          }
   	return res; 
   }
}
```

~~~java

~~~

