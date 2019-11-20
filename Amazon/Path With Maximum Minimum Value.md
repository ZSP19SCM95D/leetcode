### Path With Maximum Minimum Value

Given a matrix of integers A with `R` rows and `C` columns, find the **maximum score** of a path starting at `[0, 0]` and ending at `[R-1, C-1]`.

The score of a path is the **minimum value** in that path. For example, the value of the path `8 → 4 → 5 → 9` is `4`.

A path moves some number of times from one visited cell to any neighbouring unvisited cell in one of the `4` cardinal directions (north, east, west, south).





~~~java
public static int maximumMinimumPath(int[][] matrix) {
                if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
                        return 0;
                }
                int n = matrix.length;
                int m = matrix[0].length;
                int[][] dp = new int[n][m];
                dp[0][0] = matrix[0][0];
                for (int i = 1; i < n; i++) {
                        dp[i][0] = Math.min(dp[i - 1][0], matrix[i][0]);
                }
                for (int i = 1; i < m; i++) {
                        dp[0][i] = Math.min(dp[0][i - 1], matrix[0][i]);
                }
                for (int i = 1; i < n; i++) {
                        for (int j = 1; j < m; j++) {
                                dp[i][j] = Math.min(Math.max(dp[i - 1][j], dp[i][j - 1]),
                                                matrix[i][j]);
                        }
                }
                return dp[n - 1][m - 1];
        }
~~~

