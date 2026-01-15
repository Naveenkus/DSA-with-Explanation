## Problem
Given an array of integers `nums` and an integer `target`,
return indices of the two numbers such that they add up to `target`.

You may assume that each input has exactly one solution,
and you may not use the same element twice.

---

## Approach 1: Brute Force

### Idea
Check every possible pair of elements in the array and see
if their sum equals the given target.

### Algorithm
1. Use two nested loops.
2. Fix the first element at index `i`.
3. Check all elements after it using index `j`.
4. If `nums[i] + nums[j] == target`, return `{i, j}`.

### Code (Java)
```java
public int[] twoSum(int[] nums, int target) {
    for (int i = 0; i < nums.length - 1; i++) {
        for (int j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] == target) {
                return new int[]{i, j};
            }
        }
    }
    return new int[]{-1, -1};
}
```

## Complexity (Approach 1: Brute Force)

- **Time Complexity:** O(n²)
- **Space Complexity:** O(1)

---

## Approach 2: Optimized Using HashMap

### Observation
If two numbers add up to the target: `nums[i] + nums[j] == target` then `nums[j] = target - nums[i]`

---

### Idea
Use a HashMap to store elements and their indices.  
While traversing the array, check if the required complement already exists.

---

### Algorithm
1. Create a HashMap to store `value → index`.
2. Traverse the array from left to right.
3. For each element, calculate `target - nums[i]`.
4. If the complement exists in the map, return indices.
5. Otherwise, store the current element in the map.

---

### Code (Java)
```java
import java.util.HashMap;

public int[] twoSum(int[] nums, int target) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        int rem = target - nums[i];

        if (map.containsKey(rem)) {
            return new int[]{map.get(rem), i};
        }
        map.put(nums[i], i);
    }
    return new int[]{-1, -1};
}
```

## Complexity (Approach 1: Brute Force)

- **Time Complexity:** O(n)
- **Space Complexity:** O(n)



