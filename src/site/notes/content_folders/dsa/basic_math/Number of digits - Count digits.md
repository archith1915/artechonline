---
{"dg-publish":true,"permalink":"/content-folders/dsa/basic-math/number-of-digits-count-digits/","dgShowToc":true}
---


| **Title**     | Number of digits                                   |
| ------------- | -------------------------------------------------- |
| **Platform**  | Coding Ninjas, VSCode                              |
| **Reference** | Strivers                                           |
| **Tags**      | #dsa #math #vsc #codingninjas #strivers #cplusplus |
# Concept

### Objective: 

Count the number of digits in a given number. Say 7789.

### Solution:

Given a number, the last digit can be obtained by performing modulus 10 on it. In 7789, a modulus 10 operation will return 9 as the reminder after 7780 is evenly divided by 10. Further the number is divided by 10, thus giving 778. Repeat the same until the last digit is returned. While looping, have a count variable incremented in each loop iteration.

# Code

```c++
#include <iostream>

using namespace std;

  

int main()

{

    int num;

    cout << "Enter the number\n";

    cin >> num;

    int count = 0;

    while (num > 0)

    {

        int ld = num % 10;

        num = num / 10;

        count += 1;

        cout << ld << "\n";

    }

    cout << "The number of digits is: " << count;

}
```

#### Execution:

- In the first iteration, 9 is returned after the first modulus operation and the count variable is incremented, the number is further divided by 10 and is now 778.
- In the second iteration, 8 is returned in the modulus, count is incremented, divided by 10 to return 77.
- In the third iteration, 7 is returned in the modulus, count is incremented, divided by 10 to return 7.
- In the fourth iteration, 7 is returned in the modulus,  count is incremented, divided by 10 to return 0 (num is of integer type).
- The fifth iteration is not performed as the while condition is not satisfied.

# Time complexity

The time complexity for the above code is $O( log_{10} (N) )$ since the number is divided by 10 in each iteration. Further explanation provided in [[content_folders/dsa/time_complexity/TC - Basics\|TC - Basics]] file.





---
*Created : .*
*Last Modified : .*