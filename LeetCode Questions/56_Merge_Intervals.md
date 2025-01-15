# 56. Merge Intervals

### Approach:
We begin by sorting the input 2D array intervals based on the starting value of each interval. This is achieved using the Arrays.sort() method and a custom comparator that compares the first element of each interval. After sorting, the algorithm initializes an ArrayList<int[]> result to hold the merged intervals and sets the first interval as the initial "previous" interval (prev). It then iterates through the remaining intervals, checking if the current interval overlaps with the "previous" one. If an overlap exists (i.e., the start of the current interval is less than or equal to the end of the previous interval), the two intervals are merged by updating the end of the prev interval to the maximum of its current end and the end of the current interval. If no overlap exists, the prev interval is added to the result list, and the prev interval is updated to the current interval. Once all intervals have been processed, the last interval (prev) is added to the result. Finally, the method returns the result as a 2D array by converting the ArrayList<int[]> into an int[][] array. This approach ensures that overlapping intervals are merged, and the non-overlapping intervals are retained in the final output.

### Code:
```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        ArrayList<int[]> result = new ArrayList<>();
        int[] prev = intervals[0];
        for (int i = 1; i < intervals.length; i++) {
            int[] interval = intervals[i];
            if (interval[0] <= prev[1]) {
                prev[1] = Math.max(prev[1], interval[1]);
            }
            else {
                result.add(prev);
                prev = interval;
            }
        }
        result.add(prev);
        return result.toArray(new int[result.size()][]);
    }
}
```