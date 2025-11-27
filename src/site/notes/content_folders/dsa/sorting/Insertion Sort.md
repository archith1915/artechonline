---
{"dg-publish":true,"permalink":"/content-folders/dsa/sorting/insertion-sort/","dgShowToc":true}
---


| **Title**     | Insertion Sort                                     |
| ------------- | -------------------------------------------------- |
| **Platform**  | VSCode, LeetCode                                   |
| **Reference** | Strivers                                           |
| **Tags**      | #dsa #math #leetcode #vsc #strivers #java #sorting |
# Concept

#### Objective: 

To sort an array by comparing the elements of the subarrays at once and sort them iteratively.

### Solution:

Swap adjacent elements while pushing the largest element to the end of the array.
# Code

```java
import java.util.Arrays;


public class insertionSort {

    public static void main(String args[]) {

        int arr[] = { 13, 1, 109, 66, 3, 15, 678, 100, 102, 45, 7, 87, 0 };

  

        for (int i = 0; i <= arr.length - 1; i++) {

            int j = i;

            while (j > 0 && arr[j - 1] > arr[j]) {

                int temp = arr[j];

                arr[j] = arr[j - 1];

                arr[j - 1] = temp;

                j--;

            }

        }

  

        System.out.println(Arrays.toString(arr));

    }

}
```


#### Execution:

The algorithm uses two loops with variables *i* and *j* in each iteration for swapping. 

### **Initial Array:**

`[2, 22, 4, 0, 19, 99, 7]`

**Algorithm Reminder:**  
In each pass (_i_), Bubble Sort compares **adjacent elements** and swaps them if they are out of order.  
After each full pass, the **largest element “bubbles up”** to its correct position at the end.

---
## **Iteration 0 (i = 6)**

- Outer loop: `i = 6` → we consider indexes 0..6 (full array)
- Inner loop: `j = 0..5` → compare `arr[j]` with `arr[j+1]`

| j   | Compare `arr[j] > arr[j+1]`? | Action | Array after step         |
| --- | ---------------------------- | ------ | ------------------------ |
| 0   | 2 > 22 ? false               | —      | [2, 22, 4, 0, 19, 99, 7] |
| 1   | 22 > 4 ? true                | swap   | [2, 4, 22, 0, 19, 99, 7] |
| 2   | 22 > 0 ? true                | swap   | [2, 4, 0, 22, 19, 99, 7] |
| 3   | 22 > 19 ? true               | swap   | [2, 4, 0, 19, 22, 99, 7] |
| 4   | 22 > 99 ? false              | —      | [2, 4, 0, 19, 22, 99, 7] |
| 5   | 99 > 7 ? true                | swap   | [2, 4, 0, 19, 22, 7, 99] |

- Largest element `99` has bubbled to the end.

---
## **Iteration 1 (i = 5)**

- Outer loop: `i = 5` → consider indexes 0..5   
- Inner loop: `j = 0..4`

| j   | Compare         | Action | Array                    |
| --- | --------------- | ------ | ------------------------ |
| 0   | 2 > 4 ? false   | —      | [2, 4, 0, 19, 22, 7, 99] |
| 1   | 4 > 0 ? true    | swap   | [2, 0, 4, 19, 22, 7, 99] |
| 2   | 4 > 19 ? false  | —      | [2, 0, 4, 19, 22, 7, 99] |
| 3   | 19 > 22 ? false | —      | [2, 0, 4, 19, 22, 7, 99] |
| 4   | 22 > 7 ? true   | swap   | [2, 0, 4, 19, 7, 22, 99] |

- Second largest element `22` now in correct place.

---
## **Iteration 2 (i = 4)**

- Outer loop: `i = 4` → indexes 0..4
- Inner loop: `j = 0..3`

|j|Compare|Action|Array|
|---|---|---|---|
|0|2 > 0 ? true|swap|[0, 2, 4, 19, 7, 22, 99]|
|1|2 > 4 ? false|—|[0, 2, 4, 19, 7, 22, 99]|
|2|4 > 19 ? false|—|[0, 2, 4, 19, 7, 22, 99]|
|3|19 > 7 ? true|swap|[0, 2, 4, 7, 19, 22, 99]|

- Third largest `19` is in place.

---
## **Iteration 3 (i = 3)**

- Outer loop: `i = 3` → indexes 0..3
- Inner loop: `j = 0..2`

| j   | Compare       | Action | Array                    |
| --- | ------------- | ------ | ------------------------ |
| 0   | 0 > 2 ? false | —      | [0, 2, 4, 7, 19, 22, 99] |
| 1   | 2 > 4 ? false | —      | [0, 2, 4, 7, 19, 22, 99] |
| 2   | 4 > 7 ? false | —      | [0, 2, 4, 7, 19, 22, 99] |

- Already sorted, no swaps needed.

---
## **Iteration 4 (i = 2)**

- Outer loop: `i = 2` → indexes 0..2
- Inner loop: `j = 0..1`

| j   | Compare       | Action | Array                    |
| --- | ------------- | ------ | ------------------------ |
| 0   | 0 > 2 ? false | —      | [0, 2, 4, 7, 19, 22, 99] |
| 1   | 2 > 4 ? false | —      | [0, 2, 4, 7, 19, 22, 99] |

- No swaps.

---
## **Iteration 5 (i = 1)**

- Outer loop: `i = 1` → index 0..1
- Inner loop: `j = 0`

|j|Compare|Action|Array|
|---|---|---|---|
|0|0 > 2 ? false|—|[0, 2, 4, 7, 19, 22, 99]|

- No swaps.

---
### **Final Sorted Array:**

`[0, 2, 4, 7, 19, 22, 99]`


# Time complexity

The time complexity for the above code is $O(N)$ in best (already sorted), $O(N^2)$ in worst (reverse) and $O(N^2)$ average cases.




---
*Created : .*
*Last Modified : .*