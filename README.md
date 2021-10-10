# Best Meeting Point

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
