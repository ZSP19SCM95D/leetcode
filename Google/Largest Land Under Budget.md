**Question 1:**
Given a list of land plots with their prices and a maximum budget, find the size of largest contiguous plot of land you can purchase under the given budget.

**Example:**

```
Input: [1, 1, 3, 2, 4, 3, 2], budget = 7
Output: 4
Explanation: [1, 1, 3, 2]
```

Solution for Question 1:

~~~java
Class Solution{
  public int largestPlot(int[] plotPrices, int budget){
    int max =0;
    int budget_cur = 0;
    int hi =0;
    int low = 0;
    
    while(hi<plotPrices.length){
      if(plotPrices[hi]>=budget){
        max =Math.max(max,1);
        hi++;
        low = hi+1;
      }
      else if(budget > budget_cur){
        budget_cur += plotPrices[hi];
        hi++;
      }
      else if(budget < budget_cur){
        budget_cur -= plotPrices[low];
        low++;
      }
      else if(budget == budget_cur){
         max = Math.max(max,hi-low);
      }
     
    }
    return max;
  }
}
~~~



**Question 2:**
Given a 2D array representing a 2D plot of land, find the maximum side length of a square plot of land under the budget.

**Example:**

```
Input:
[[1, 1, 3, 2, 4, 3, 2]
 [1, 1, 3, 2, 4, 3, 2]
 [1, 1, 3, 2, 4, 3, 2]]
budget = 4

Output: 2
Explanation:
[[1, 1],
 [1, 1]]
```

~~~java

~~~

