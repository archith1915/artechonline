---
{"dg-publish":true,"permalink":"/public/content-folders/dsa/basic-math/reverse-a-number/","dgShowToc":true}
---

| **Title**     | Reverse a number                                             |
| ------------- | ------------------------------------------------------------ |
| **Platform**  | LeetCode, Coding Ninjas, VSCode                              |
| **Reference** | Strivers                                                     |
| **Tags**      | #dsa #math #vsc #leetcode #codingninjas #strivers #cplusplus |
# Concept

#### Objective: 

The objective of this problem is to reverse a given number. Say 1234.

### Solution:

We solve this using the digit extraction approach used in [[public/content_folders/dsa/basic_math/Number of digits - Count digits\|Number of digits - Count digits]] problem. The digits are extracted one by one and then added to a new variable. The reverser number variable is multiplied by 10 and the last digit obtained by the modulus operation is added to it.

# Code

```c++
#include <iostream>

using namespace std;

  

int main()

{

    long long number, count = 0, lastDigit, revNum = 0;

    cout << "Enter a number: ";

    cin >> number;

  

    while (number > 0)

    {

        lastDigit = number % 10;

        revNum = revNum * 10 + lastDigit;

        number = number / 10;

    }

  

    cout << "The reversed number is : " << revNum;

}
```

#### Execution:

- In the first iteration, the last digit 4 is returned. The revNum, initially zero is multiplied by 10 which gives back 0. The lastDigit 4 is added to this zero.
- In the next iteration the next digit, 3 is returned, the revNum is again multiplied by 10, this time giving 40 and 3 is added. Now, revNum = 43.
- In the third iteration, the next digit, 2 is returned. revNum is multiplied by 10 giving 430, 2 is added to it resulting in revNum = 432.
- In the last iteration, 1 is returned, revNum becomes 4320 and 1 is added giving us revNum = 4321. The loop stops here as the while condition is not satisfied anymore.

# Time complexity

The time complexity for the above code is $O( log_{10} (N) )$ since the number is divided by 10 in each iteration. Further explanation provided in [[public/content_folders/dsa/time_complexity/TC - Basics\|TC - Basics]] file.





---
*Created : .*
*Last Modified : .*