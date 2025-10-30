---
{"dg-publish":true,"permalink":"/content-folders/dsa/blind75/two-sum/","title":"Two Sum","tags":["dsa","leetcode","blind75","strivers"],"dgShowToc":true}
---

The objective in two sum problem is to find two numbers, say *x* and *y*, in a given array 'arr' such that x and y add up to a given target number *z*. While the simplest approach to this problem is brute force using two loops to check for the sum, it's time complexity happens to be on the higher side.

An alternate approach with a better time complexity is to solve it using hashmaps. A hashmap can be used to store the elements of the array along with their indexes. Hashmaps, being very quick in retrieving elements given their key can help reduce the time complexity by a huge factor.

**Implementation**

```java
import java.util.HashMap;

import java.util.Arrays;

  

public class twoSum {

    public static int[] findTwoSum(int[] arr, int target) {

        HashMap<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < arr.length; i++) {

            int complement = target - arr[i];

  

            if (map.containsKey(complement)) {

                return new int[] { map.get(complement), i };

            } else {

                map.put(arr[i], i);

            }

  

        }

        return new int[] { -1, -1 };

    }

  
    public static void main(String[] args) {

        int arr[] = { 3, 15, 6, 18, 66, 14, 1 };

        int target = 19;

  

        int result[] = findTwoSum(arr, target);

  

        if (result[0] == -1) {

            System.out.println("No pairs found");

        } else {

            System.out.println(Arrays.toString(result));

        }

    }

}

```

**Explanation**

- The findTwoSum function takes an array and the target as parameters and calculates the difference between the current element in the array and the required target.
- It then checks if the complement exists in the hashmap, if it does, the index is returned.
- Else, the element along with its index is added to the hashmap.

**Example**

Let the array be {2,4,5,8,10,9,11} and the target be 9

In the first iteration element 2 is chosen from the array and the complement is calculated, 7. The program checks if 7 exists in the hashmap. Currently the hashmap is empty, hence the key-value pair (2,0) is pushed into the hashmap.

During the second iteration, 4 is chosen, the complement will be 5. Since 5 does not exist in the hashmap, (4,0) pair is added to the hashmap.

During the third iteration, 5 is chosen from the array. The complement this time is 4. The program checks if 4 exists in the hashmap. Since it does, an array of the indexes of 4 and 5 (1, 2) is returned.