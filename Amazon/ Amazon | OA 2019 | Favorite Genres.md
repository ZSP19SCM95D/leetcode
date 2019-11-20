### Amazon | OA 2019 | Favorite Genres

Given a map `Map<String, List<String>> userSongs` with user names as keys and a list of all the songs that the user has listened to as values.

Also given a map `Map<String, List<String>> songGenres`, with song genre as keys and a list of all the songs within that genre as values. The song can only belong to only one genre.

The task is to return a map `Map<String, List<String>>`, where the key is a user name and the value is a list of the user's favorite genre(s). Favorite genre is the most listened to genre. A user can have more than one favorite genre if he/she has listened to the same number of songs per each of the genres.



**Example 1:**

```java
Input:
userSongs = {  
   "David": ["song1", "song2", "song3", "song4", "song8"],
   "Emma":  ["song5", "song6", "song7"]
},
songGenres = {  
   "Rock":    ["song1", "song3"],
   "Dubstep": ["song7"],
   "Techno":  ["song2", "song4"],
   "Pop":     ["song5", "song6"],
   "Jazz":    ["song8", "song9"]
}

Output: {  
   "David": ["Rock", "Techno"],
   "Emma":  ["Pop"]
}

Explanation:
David has 2 Rock, 2 Techno and 1 Jazz song. So he has 2 favorite genres.
Emma has 2 Pop and 1 Dubstep song. Pop is Emma's favorite genre.
```

**Example 2:**

```java
Input:
userSongs = {  
   "David": ["song1", "song2"],
   "Emma":  ["song3", "song4"]
},
songGenres = {}

Output: {  
   "David": [],
   "Emma":  []
}
```

~~~java
public static Map<String, List<String>> findGenres (Map<String, List<String>> userSongs, Map<String, List<String>> songGenres) {
        Map<String, List<String>> output = new HashMap<>();

        if (songGenres.size() == 0) {
            for (Map.Entry<String, List<String>> entry : userSongs.entrySet()) {
                output.put(entry.getKey(), new ArrayList<>());
            }
            return output;
        }

        // Creating new HashMap with song to genre mapping
        Map<String, String> songs = new HashMap<>();
        for (Map.Entry<String, List<String>> entry : songGenres.entrySet()){
            for (String song : entry.getValue()) {
                songs.put(song, entry.getKey());
            }
        }
        
        Map<String, Integer> genres = new HashMap<>();

        for (Map.Entry<String, List<String>> entry : userSongs.entrySet()) {
            genres.clear();
            for (String song : entry.getValue()) {
                genres.put(songs.get(song), genres.getOrDefault(songs.get(song), 0) + 1);
            }

            int max = 0;
            List<String> list = new ArrayList<>();
            for (Map.Entry<String, Integer> newEntry : genres.entrySet()) {
                if (newEntry.getValue() > max) {
                    max = newEntry.getValue();
                    list.clear();
                    list.add(newEntry.getKey());
                } else if (newEntry.getValue() == max) { list.add(newEntry.getKey()); }
            }
            output.put(entry.getKey(), list);
        }
        return output;
    }
~~~

