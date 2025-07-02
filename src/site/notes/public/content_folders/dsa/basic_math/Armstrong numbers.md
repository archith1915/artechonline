---
{"dg-publish":true,"permalink":"/public/content-folders/dsa/basic-math/armstrong-numbers/","dgShowToc":true}
---

| **Title**     | Armstsrong numbers                                 |
| ------------- | -------------------------------------------------- |
| **Platform**  | VSCode, Coding Ninjas                              |
| **Reference** | Strivers                                           |
| **Tags**      | #dsa #codingninjas #vsc #math #strivers #cplusplus |
# Concept

#### Objective: 

An **Armstrong number** (also known as a narcissistic number) is a number that is equal to the sum of its own digits each raised to the power of the number of digits. The objective of this problem is to check if the given number is armstrong.

### Solution:

We count the number of digits in the given number using the [[public/content_folders/dsa/basic_math/Number of digits - Count digits\|Number of digits - Count digits]] algorithm. As each digit is returned, we raise it to the power of the number of digits and calculate the summation. Further this summation is compared to the given number. If equal, armstrong. Else, not an armstrong.

# Code

```c++
#include <iostream>

#include <cmath>

using namespace std;

  

int main()

{

    long long number, lastDigit, sum = 0, count = 0;

    cout << "Enter the number: ";

    cin >> number;

    int num = number, duplicate = number;

  

    while (duplicate > 0)

    {

        int ld = duplicate % 10;

        count += 1;

        duplicate = duplicate / 10;

    }

  

    cout << "The total number of digits is: " << count << "\n";

  

    while (num > 0)

    {

        lastDigit = num % 10;

        sum = sum + round(pow(lastDigit, count));

        num = num / 10;

        cout << "The summation for digit: " << lastDigit << " is : " << sum << "\n";

    }

  

    cout << "The summation is: " << sum << "\n";

    if (sum == number)

    {

        cout << "The given number is an armstrong";

    }

    else

    {

        cout << "The given number is not an armstrong";

    }

}
```


#### Execution:

The execution here is similar to that in [[public/content_folders/dsa/basic_math/Number of digits - Count digits\|Number of digits - Count digits]]

Read the execution section here : [[public/content_folders/dsa/basic_math/Number of digits - Count digits#Execution\|Execution of number of digits algorithm]].

- Once the number of digits are obtained in the first while loop, another while loop is initiated to calculate the summation. Each time a digit is returned, it is raised to the power of count and added to the summation variable, thus calculating the summation of all the digits in the number.
- For an armstrong number 153, in the first iteration, it is 0 + 3^3. Which results in 27.
- In the next iteration, 27 + 5^3 = 152. In the final iteration the third power of 1 is added to the summation variable, thus completing the loop.
- The actual input and the calculated summation are now compared to determine whether the input number is armstrong or not.

>*Note:* In C++, the round() must be used for the power calculation as the pow() function returns a double datatype though it is an exact integer which may lead to incorrect decisions by the if statement.

# Time complexity

The time complexity for the above code is $O( log_{10} (N) )$ since the number is divided by 10 in each iteration. Further explanation provided in [[public/content_folders/dsa/time_complexity/TC - Basics\|TC - Basics]] file.





---
*Created : .*
*Last Modified : .*