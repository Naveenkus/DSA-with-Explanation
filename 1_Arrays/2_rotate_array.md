## Problem
Given an array `arr[]`, rotate the array to the left (counter-clockwise direction)
by `d` steps, where `d` is a positive integer.

The rotation should be done **in-place**.

---
**Source:** GeeksforGeeks  
**Difficulty:** Medium  

## Approach 1: Brute Force (Using Extra Space)

### Idea
Store the first `d` elements in a temporary array.
Shift the remaining elements of the array to the left.
Finally, copy the stored elements from the temporary array
to the end of the original array.

---

### Algorithm
1. Let `n` be the size of the array.
2. Normalize `d` using `d = d % n`.
3. Create a temporary array `temp` of size `d`.
4. Copy the first `d` elements of `arr` into `temp`.
5. Shift elements from index `d` to `n-1` to the left by `d` positions.
6. Copy elements from `temp` into the last `d` positions of `arr`.

---

### Code (Java)
```java
class Solution {
    static void rotateArr(int arr[], int d) {
        int n = arr.length;
        d = d % n;
        if (d == 0) return;

        int[] temp = new int[d];
        int rem = n - d;

        for (int i = 0; i < d; i++) {
            temp[i] = arr[i];
        }

        for (int i = d; i < n; i++) {
            arr[i - d] = arr[i];
        }

        for (int i = 0; i < d; i++) {
            arr[rem + i] = temp[i];
        }
    }
}
```
## Complexity (Approach 1)

- **Time Complexity:** O(n)
- **Space Complexity:** O(d)

---

## Approach 2: Optimized Using Reversal Algorithm

### Idea
A left rotation can be achieved by reversing parts of the array:

- Reverse the first `d` elements
- Reverse the remaining `n - d` elements
- Reverse the entire array

This performs the rotation **in-place** without using extra space.

---

### Algorithm
1. Normalize `d` using `d = d % n`.
2. Reverse the subarray from index `0` to `d - 1`.
3. Reverse the subarray from index `d` to `n - 1`.
4. Reverse the entire array from index `0` to `n - 1`.

---

### Code (Java)
```java
class Solution {
    static void rotateArr(int arr[], int d) {
        int n = arr.length;
        d = d % n;
        if (d == 0) return;

        reverse(arr, 0, d - 1);
        reverse(arr, d, n - 1);
        reverse(arr, 0, n - 1);
    }

    private static void reverse(int arr[], int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;

            start++;
            end--;
        }
    }
}

```
## Complexity (Approach 1)

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)
