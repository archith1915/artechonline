---
{"dg-publish":true,"permalink":"/content-folders/dsa/blind75/contains-duplicate/","title":"Contains Duplicate","tags":["blind75","leetcode","level-easy"]}
---


| **Title**     | Contains Duplicate                          |
| ------------- | ------------------------------------------- |
| **Platform**  | VSCode, LeetCode                            |
| **Reference** | Strivers                                    |
| **Tags**      | #dsa #array #leetcode #vsc #strivers #java  |

---


The objective is to find whether an array contains duplicate elements. The optimal approach uses a hashset to remove duplicates from an array. The size of the array and hashset are compared to conclude 

```java
import java.util.HashSet;

  

public class duplicates {

    public static boolean findDuplicates(int[] arr) {

        HashSet<Integer> set = new HashSet<>();

  

        for (int i : arr) {

            set.add(i);

        }

  

        if (set.size() < arr.length) {

            System.out.println("Size of the set is " + set.size());

            System.out.println("Size of the array is " + arr.length);

            System.out.println("The number of duplicates is " + (arr.length - set.size()));

            return true;

        } else {

            System.out.println("Size of the set is " + set.size());

            System.out.println("Size of the array is " + arr.length);

            return false;

        }

    }

  

    public static void main(String[] args) {

        int[] arr = { 2, 1, 4, 6, 7, 8, 9, 1, 2, 10, 11 };

        boolean result = findDuplicates(arr);

        System.out.println(result);

    }

}
```