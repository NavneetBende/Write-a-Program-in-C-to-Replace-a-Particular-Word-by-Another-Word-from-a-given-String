Replace a Particular word by Another word from a Given String in C
Here, in this page we will discuss the program to Replace a Particular word by Another word from a Given String in C programming language.

Replace a Particular word by Another word from a Given String in C
While loop in C
Example
Input :
Given String, str[] = "Let's Learn C++"
old_word[] = "C++"
new_word[] = "C"
Output :
Let's Learn C
Algorithm :
Traverse the original string.
Counting the number of times the old term appears.
Make a new string of sufficient length to replace the new word.
Now replace the word in the old string with the new string.
Code in C
Run
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
  
// Function to replace a string with another string
char* replaceWord(const char* s, const char* old_word, const char* new_word)
{
    char* result;
    int i, cnt = 0;
    int newWlen = strlen(new_word);
    int oldWlen = strlen(old_word);
  
    // Counting the number of times old word
    // occur in the string
    for (i = 0; s[i] != '\0'; i++) {
        if (strstr(&s[i], old_word) == &s[i]) {
            cnt++;
  
            // Jumping to index after the old word.
            i += oldWlen - 1;
        }
    }
  
    // Making new string of enough length
    result = (char*)malloc(i + cnt * (newWlen - oldWlen) + 1);
  
    i = 0;
    while (*s) {
        // compare the substring with the result
        if (strstr(s, old_word) == s) {
            strcpy(&result[i], new_word);
            i += newWlen;
            s += oldWlen;
        }
        else
            result[i++] = *s++;
    }
  
    result[i] = '\0';
    return result;
}
  
// Driver Program
int main()
{
    char str[] = "Let's Learn C++";
    char c[] = "C++";
    char d[] = "C";
  
    char* result = NULL;
  
    // oldW string
    result = replaceWord(str, c, d);
    printf("Old String: %s\n", str);
    printf("New String: %s\n", result);
  
    return 0;
}
Output
Old String: Let's Learn C++
New String: Let's Learn C
