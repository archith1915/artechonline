---
{"dg-publish":true,"permalink":"/content-folders/dsa/basic-math/check-for-prime/","dgShowLocalGraph":true,"dgShowToc":true}
---

| **Title**     | Check for prime |
| ------------- | --------------- |
| **Platform**  | VSCode          |
| **Reference** | Strivers        |
| **Tags**      | #dsa #vsc #math |
# Concept

#### Objective: 

Given a number, check if it is a prime.
### Solution:

A common misconception is that primes are those with only one and itself as it's divisors, which makes 1 a prime while it is not. The most accurate definition for a prime would be, a number with exactly two divisors: 1 and itself. To find the divisors we use the [[content_folders/dsa/basic_math/All divisors of a number\|All divisors of a number]] algorithm and count the number of divisors. If the number of divisors if exactly 2, it is a prime. Else, it is not.

# Code

```
#include <iostream>

#include <cmath>

using namespace std;

  

int main()

{

    int number, count = 0;

    cout << "Enter the number : ";

    cin >> number;

    cout << "The divisors for " << number << " are: ";

    for (int i = 1; i <= sqrt(number); i++)

    {

        if (number % i == 0)

        {

            cout << i << " ";

            count += 1;

        }

  

        if (number / i != i)

        {

            cout << number / i << " ";

            count += 1;

        }

    }

  

    cout << "\nThe number of divisors for " << number << " are: " << count;

  

    if (count == 2)

    {

        cout << "\nThe given number is a prime";

    }

    else

    {

        cout << "\nThe given number is not a prime";

    }

}
```


#### Execution:

The divisors for the given number are obtained using the [[content_folders/dsa/basic_math/All divisors of a number\|All divisors of a number]] algorithm.

Read the execution section here: [[content_folders/dsa/basic_math/All divisors of a number#Execution\|Execution of all divisors of a number algorithm]].

- Once the count of the divisors is available, an if condition checks if the count is exactly two and decides whether it is a prime or not.

# Time complexity

The time complexity of this algorithm is $O( \sqrt(N) )$ while the complexity for the brute force method is $ O( log_{10} (N)) $