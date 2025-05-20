# EX 4D DYNAMIC PROGRAMMING – 4
## DATE:
## AIM:
To find the minimum number of operations to convert str1 to str2 using Naive recursive method.

## Algorithm
1. Read the input string s and create a 2D table dp of size len(s) x len(s), initialized with False.
2. Set dp[i][i] = True for all i, since each single character is a palindrome.
3. Initialize two variables: max_length = 1 and start = 0 to keep track of the longest palindromic substring found.
4. For each possible substring length l from 2 to len(s), iterate over all starting indices i and calculate end = i + l.
5. If s[i] == s[end-1] and either the length is 2 or the inner substring dp[i+1][end-2] is True, mark dp[i][end-1] = True, and if the new palindrome is longer, update start and max_length.
6.After all iterations, return the substring s[start : start + max_length] as the longest palindromic substring.

## Program:
```
/*
Program to implement to find the minimum number of operations to convert str1 to str2 using Naive recursive method

Developed by: REXLIN R
Register Number:  212222220034
*/
class Solution(object):
    def longestPalindrome(self, s):
    ###########  Add your code here #############
        dp = [[False for i in range(len(s))] for i in range(len(s))]
        for i in range(len(s)):
            dp[i][i] = True
        max_length = 1
        start = 0
        for l in range(2,len(s)+1):
             for i in range(len(s)-l+1):
                end = i+l
                if l==2:
                    if s[i] == s[end-1]:
                        dp[i][end-1]=True
                        max_length = l
                        start = i
                else:
                    if s[i] == s[end-1] and dp[i+1][end-2]:
                        dp[i][end-1]=True
                        max_length = l
                        start = i
        return s[start:start+max_length]

ob1 = Solution()
str1=input()
print(ob1.longestPalindrome(str1))
```

## Output:

![image](https://github.com/user-attachments/assets/d19dcd8f-42bc-40d0-a782-8c6184bc55ac)

## Result:
Thus the program was executed successfully for finding edit distance between two strings.
