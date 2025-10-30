---
{"dg-publish":true,"permalink":"/content-folders/javafordsa/strings/","title":"Strings","tags":["dsa","java","coreSubjects"],"dgShowToc":true}
---

```java
String name = new String ("StringValue");
```

**Constructors:**

1. String() - Default
2. String ("StringValue") - Initialize the string with the value of the string passed.
3. String (char chs\[]) - Initialize the string from the characters of the array.
4. String (String strObject) - Initialize the string with the value of another string object.
5. String (char ch\[], int startIndex, int count) - Initialize the string with the values of the character array starting from the *startIndex* counting the characters to *count*.
6. String (byte byteArray\[]) - Initializes the string to the value obtained from the ASCII values in the byte array.
7. String (byte byteArray\[], int startIndex, int count) - Initialize the string with the value obtained from the byte array starting from the *startIndex* counting the characters to *count*.

**Methods on strings:**

**Character Extraction**

| Method                                                                   | Description                                                                                                                                                               |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| length()                                                                 | Calculate the length of the string                                                                                                                                        |
| charAt(int index)                                                        | Obtain the character at the specified index in the string                                                                                                                 |
| getChars(int sourceStart, int souceEnd), char target\[], int targetStart | Extract a set of characters starting from the *sourceStart* index, all the way to the *sourceEnd* index and insert them to the *target* array at the *targetStart* index. |
| getBytes()                                                               | Extract a set of characters from the string in byte format. (Arguments similar to that of *getChars()*)                                                                   |
| toCharArray()                                                            | Convert the string into a character array.                                                                                                                                |
**String comparision**


| Method                                                                       | Description                                                                                                                                                                     |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| equals(String str/object)                                                    | Compare if two strings are the same                                                                                                                                             |
| equalsIgnoreCase(String str/object)                                          | Compares if two strings are the same but ignores cases                                                                                                                          |
| regionMatches(int startIndex, String str2, int str2StartIndex, int numChars) | Checks if the region from *startIndex* in the invoking string matches with the region from *str2StartIndex* in the second string                                                |
| startsWith(String str/object)                                                | Checks if the invoking string starts with the string passed to the function                                                                                                     |
| endsWith(String str/object)                                                  | Checks if the invoking string ends with the string passed to the function                                                                                                       |
| compareTo(String str/object)                                                 | Compares the invoking string with the string passed to return an integer value. Less than zero if invoking string is less than str, zero if equal, greater than zero if greater |
| compareToIgnoreCase(String str/ object)                                      | Compares the invoking string with the string passed to return a value similar to *compareTo()* but ignores case                                                                 |
**Searching strings**


| Method                              | Description                                                              |
| ----------------------------------- | ------------------------------------------------------------------------ |
| indexOf(Char ch) /(String str)      | Find the index(first occurrence) of the character passed to the function |
| lastIndexOf(char ch) / (String str) | Find the index (last occurrence) of the character passed to the function |

**Modifying a string**


| Method                                   | Description                                                                                                   |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| substring(int startIndex)                | Returns a substring from the invoking string from the *startIndex* index all the way to the end of the string |
| substring(int startIndex, int endIndex)  | Returns a substring from the invoking string from the *startIndex* index all the way to the *endIndex* index  |
| concat(String str)                       | Concatenate the string *str* to the invoking string                                                           |
| replace(char original, char replacement) | Replace all occurrences of the character *original* with the character *replacement*                          |
| trim()                                   | Used to remove extra spaces at the beginning and end of the invoking string                                   |
| toLowerCase()                            | Change the invoking string to lower case                                                                      |
| toUpperCase()                            | Change the invoking string to upper case                                                                      |
# StringBuffer

**Constructors:**

1. StringBuffer() - Default
2. StringBuffer(int size) - String buffer of the size *size*
3. StringBuffer(String str) - Initialize the string buffer with the string *str*

**Methods on string buffer**


| Method                                                                         | Description                                                                                                                                                               |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| length()                                                                       | Get the length of the string buffer (total number of elements)                                                                                                            |
| capacity()                                                                     | Get the total capacity of the invoking string buffer                                                                                                                      |
| ensureCapacity(int capacity)                                                   | Set a minimum capacity for the invoking string buffer                                                                                                                     |
| setLength(int len)                                                             | Set the length of the invoking string buffer to *len*                                                                                                                     |
| charAt(int index)                                                              | Get the character at the index *index*                                                                                                                                    |
| setCharAt(int index, char ch)                                                  | Set character *ch* at the index *index* in the string buffer                                                                                                              |
| getChars(int sourceStart, int sourceEnd, int target\[], int targetStart)       | Extract a set of characters starting from the *sourceStart* index, all the way to the *sourceEnd* index and insert them to the *target* array at the *targetStart* index. |
| append(String str) / (int num) / (Object obj)                                  | Concatenate the argument value to the invoking string buffer                                                                                                              |
| insert(int index, String str) / (int index, char ch) / (int index, Object obj) | Insert the argument value at the index *index* in the invoking string buffer                                                                                              |
| reverse()                                                                      | Reverse the characters in the invoking string buffer                                                                                                                      |
| delete(int startIndex, int endIndex)                                           | Delete characters in the invoking string buffer starting from the *startIndex* all the way to the *endIndex*                                                              |
| deleteCharAt(int index)                                                        | Delete character at *index* index in the invoking string buffer                                                                                                           |
| replace(int startIndex, int endIndex, String str)                              | Replace the string in the string buffer with the string *str* starting from the index *startIndex* all the way to the index *endIndex*                                    |
| substring(int startIndex) / (int startIndex, int endIndex)                     | Extract a substring from the invoking string buffer starting from the *startIndex* index all the way to the end of the buffer or till the index *endIndex*                |
