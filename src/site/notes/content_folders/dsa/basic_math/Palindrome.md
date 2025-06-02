---
{"dg-publish":true,"permalink":"/content-folders/dsa/basic-math/palindrome/","dgShowToc":true}
---


| **Title**     | Palindrome                |
| ------------- | ------------------------- |
| **Platform**  | VSCode, LeetCode          |
| **Reference** | Strivers                  |
| **Tags**      | #dsa #math #leetcode #vsc |
# Concept

#### Objective: 

To check whether a number is palindrome

### Solution:

We use the concepts discussed in [[content_folders/dsa/basic_math/Reverse a number\|Reverse a number]] problem to find out whether the given number is a palindrome. The input from the user is first stored to a duplicate variable and the number is reversed using the [[content_folders/dsa/basic_math/Reverse a number\|Reverse a number]] algorithm. The reversed number is then compared with the input stored in the duplicate variable. If equal, it is a palindrome. Else, not a palindrome.
# Code

```
#include <iostream>

using namespace std;

  

int main()

{

    int num, lastDigit = 0, revDig = 0;

    cout << "Enter a number\n";

    cin >> num;

    int number = num;

  

    while (num > 0)

    {

        lastDigit = num % 10;

        revDig = revDig * 10 + lastDigit;

        num = num / 10;

    }

    cout << revDig;

  

    if (number == revDig)

    {

        cout << "\nThe number is a palindrome";

    }

    else

    {

        cout << "\nThe number is not a palindrome";

    }

}
```


#### Execution:

Refer to the execution section in [[content_folders/dsa/basic_math/Reverse a number\|Reverse a number]] :

[[content_folders/dsa/basic_math/Reverse a number#^391cc8\|Execution of reversing a number algorithm]]

Once all the iterations are completed, an if condition compares the reverse number with the duplicate variable to check if it is a palindrome.

# Time complexity

The time complexity for the above code is $O( log_{10} (N) )$ since the number is divided by 10 in each iteration. Further explanation provided in [[content_folders/dsa/time_complexity/TC - Basics\|TC - Basics]] file.