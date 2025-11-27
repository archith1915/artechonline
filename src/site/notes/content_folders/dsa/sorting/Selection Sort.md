---
{"dg-publish":true,"permalink":"/content-folders/dsa/sorting/selection-sort/","dgShowToc":true}
---


| **Title**     | Selection Sort                                     |
| ------------- | -------------------------------------------------- |
| **Platform**  | VSCode, LeetCode                                   |
| **Reference** | Strivers                                           |
| **Tags**      | #dsa #math #leetcode #vsc #strivers #java #sorting |
# Concept

#### Objective: 

To sort the integer elements in an array using selection sort.

### Solution:

In each iteration select the minimum in each subarray and swap it with the element in the first position of the subarray until the last element is encountered.
# Code

```java
import java.util.Arrays;


public class selectionSort {

    public static void main(String args[]) {

        int arr[] = { 2, 22, 4, 0, 19, 99, 7 };

        int n = arr.length;

  

        for (int i = 0; i <= n - 2; i++) {

            int min = i;

            for (int j = i+1; j <= n - 1; j++) {

                if (arr[j] < arr[min]) {

                    int temp = arr[min];

                    arr[min] = arr[j];

                    arr[j] = temp;

                }

            }

            System.out.println("Array in iteration" + i + " is : " + Arrays.toString(arr));

        }

  

        System.out.println("Final array : ");

        System.out.println(Arrays.toString(arr));

    }

}
```


#### Execution:

The algorithm uses two loops with variables *i* and *j* and a variable *min* to store the minimum element in each iteration for swapping. As we move the smaller elements to the beginning of the array and to their appropriate positions, we exclude them in further iterations using the *i* loop while the *j* loop continues to compare and sort other elements starting from the last sorted element at *i*^th^ index 

### **Initial array:**

`[2, 22, 4, 0, 19, 99, 7]`

---
## **Iteration 0 (i = 0)**

- Start: `min = i = 0` → value = 2
- We’ll find the smallest element from index 0 → end.

|j|Compare|Condition (`arr[j] < arr[min]`)|Result|min|
|---|---|---|---|---|
|1|22 < 2|false|min stays at 0|0|
|2|4 < 2|false|min stays at 0|0|
|3|0 < 2|**true**|min becomes 3|3|
|4|19 < 0|false|—|3|
|5|99 < 0|false|—|3|
|6|7 < 0|false|—|3|

→ **min = 3**, value = 0

- Swap `arr[0]` and `arr[3]`  
→ `[0, 22, 4, 2, 19, 99, 7]`

---
## **Iteration 1 (i = 1)**

- Start: `min = i = 1` → value = 22

|j|Compare|Condition (`arr[j] < arr[min]`)|Result|min|
|---|---|---|---|---|
|2|4 < 22|**true**|min = 2|2|
|3|2 < 4|**true**|min = 3|3|
|4|19 < 2|false|—|3|
|5|99 < 2|false|—|3|
|6|7 < 2|false|—|3|

→ **min = 3**, value = 2

- Swap `arr[1]` and `arr[3]`  
→ `[0, 2, 4, 22, 19, 99, 7]`

---
## **Iteration 2 (i = 2)**

- Start: `min = i = 2` → value = 4

|j|Compare|Condition (`arr[j] < arr[min]`)|Result|min|
|---|---|---|---|---|
|3|22 < 4|false|—|2|
|4|19 < 4|false|—|2|
|5|99 < 4|false|—|2|
|6|7 < 4|false|—|2|

→ **min = 2**, value = 4 (no smaller element found)

- No swap (4 already in correct position)  
→ `[0, 2, 4, 22, 19, 99, 7]`

---
## **Iteration 3 (i = 3)**

- Start: `min = i = 3` → value = 22

|j|Compare|Condition (`arr[j] < arr[min]`)|Result|min|
|---|---|---|---|---|
|4|19 < 22|**true**|min = 4|4|
|5|99 < 19|false|—|4|
|6|7 < 19|**true**|min = 6|6|

→ **min = 6**, value = 7

- Swap `arr[3]` and `arr[6]`  
→ `[0, 2, 4, 7, 19, 99, 22]`

---
## **Iteration 4 (i = 4)**

- Start: `min = i = 4` → value = 19

|j|Compare|Condition (`arr[j] < arr[min]`)|Result|min|
|---|---|---|---|---|
|5|99 < 19|false|—|4|
|6|22 < 19|false|—|4|

→ **min = 4**, value = 19

- No swap  
→ `[0, 2, 4, 7, 19, 99, 22]`

---
## **Iteration 5 (i = 5)**

- Start: `min = i = 5` → value = 99

|j|Compare|Condition (`arr[j] < arr[min]`)|Result|min|
|---|---|---|---|---|
|6|22 < 99|**true**|min = 6|6|

→ **min = 6**, value = 22

- Swap `arr[5]` and `arr[6]`  
→ `[0, 2, 4, 7, 19, 22, 99]`

---
## **Iteration 6 (i = 6)**

- Only one element remains (99), already in place.  
- No action needed.

---
###  **Final Sorted Array:**

`[0, 2, 4, 7, 19, 22, 99]`


# Time complexity

The time complexity for the above code is $O(N^2)$ in best, worst and average cases.




---
*Created : .*
*Last Modified : .*