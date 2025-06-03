---
{"dg-publish":true,"permalink":"/content-folders/dsa/basic-math/all-divisors-of-a-number/","dgShowToc":true}
---


| **Title**     | All divisors of a number                           |
| ------------- | -------------------------------------------------- |
| **Platform**  | VSCode, Coding Ninjas                              |
| **Reference** | Strivers                                           |
| **Tags**      | #dsa #codingninjas #vsc #math #strivers #cplusplus |
# Concept

#### Objective: 

Given a number, the objective is to find all the numbers that divide it completely.

### Solution:

For any number, the divisors start from 1 x itself and end at itself x 1. The easiest approach is to run a loop to check all the numbers that give out a zero reminder using the modulus operation. But this brute force method is expensive in terms of time and computational efforts. A simpler approach can be derived with a simple understanding of the cycle of the divisors from 1 x number to number x 1.

Assume that the number given is 36. The divisors are:
- 1 x 36
- 2 x 18
- 3 x 12
- 4 x 9
- ***6 x 6***
- 9 x 4
- 12 x 3
- 18 x 2
- 36 x 1

In the cycle above, it can be seen that all the combinations after 6 x 6, the square root of 36, are just replicas of the combinations before 6 x 6. Hence, it is efficient to run the loop only till the square root of the number and list out all the unique numbers as the divisors of the given number.

>*Note:* The last entry in the loop 6 x 6, will give us two entries for 6, hence, a condition to check for uniqueness must be included in the loop.

# Code

```c++
#include <iostream>

#include <cmath>

using namespace std;

  

int main()

{

    int number;

    cout << "Enter the number: ";

    cin >> number;

  

    for (int i = 1; i <= sqrt(number); i++)

    {

        if (number % i == 0)

        {

            cout << i << " ";

  

            if ((number / i) != i)

            {

                cout << number / i << " ";

            }

        }

    }

  

    return 0;

}
```


#### Execution:

- The for loop runs from 1 all the way till the square root of the given number. Note that the loop cannot start from zero (division by zero error). 
- The first if condition checks if the modulus operation gives out a zero reminder, if yes, print the number as a divisor. Else, skip.
- The second if condition checks for the next possible divisor while also making sure that there are no repetitions in the divisors being printed.

# Time complexity

The time complexity of this algorithm is $O( \sqrt(N) )$ while the complexity for the brute force method is $O( log_{10} (N))$





---
*Created : .*
*Last Modified : .*