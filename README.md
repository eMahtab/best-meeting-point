# Best Meeting Point
Given an m x n binary grid grid where each 1 marks the home of one friend, return the minimal total travel distance.

The total travel distance is the sum of the distances between the houses of the friends and the meeting point.

The distance is calculated using Manhattan Distance, where distance(p1, p2) = |p2.x - p1.x| + |p2.y - p1.y|.

!["Best Meeting Point"](example.JPG?raw=true)

```
Constraints:

1. m == grid.length
2. n == grid[i].length
3. 1 <= m, n <= 200
4. grid[i][j] is either 0 or 1.
5. There will be at least two friends in the grid.
```

# Implementation 1 : Time Limit Exceeded
```java
class Solution {
    public int minTotalDistance(int[][] grid) {
        if(grid == null || grid.length == 0)
            return 0;
        int rows = grid.length;
        int cols = grid[0].length;
        List<int[]> houses = new ArrayList<>();
        for(int i = 0; i < rows; i++) {
            for(int j = 0; j < cols; j++) {
                if(grid[i][j] == 1) {
                    houses.add(new int[]{i,j});
                }
            }
        }
        int minDistance = Integer.MAX_VALUE;
        for(int i = 0; i < rows; i++) {
            for(int j= 0; j < cols; j++) {
                int distance = getDistanceFromHouses(grid, i, j, houses);
                minDistance = Math.min(minDistance, distance);
            }
        }
        return minDistance;
    }
    
    public int getDistanceFromHouses(int[][] grid, int row, int col, List<int[]> houses) {
        int totalDistance = 0;
        for(int[] house : houses) {
            int distance = Math.abs(row - house[0]) + Math.abs(col - house[1]);
            totalDistance += distance;
        }
        return totalDistance;
    }
}
```
