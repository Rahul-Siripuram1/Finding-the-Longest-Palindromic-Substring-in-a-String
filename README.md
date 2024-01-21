# Finding-the-Longest-Palindromic-Substring-in-a-String


Palindrome Definition:

A palindrome is a sequence of characters that reads the same forward as backward.
Input:

The input is a string s consisting of lowercase and/or uppercase letters, and it may contain spaces and other non-alphabetic characters.
Output:

The function should return a string, which is the longest palindromic substring found in the input string.
Handling Multiple Palindromes:

If there are multiple palindromes with the same length, the function should return the one that appears first in the input string.
Example:

For example, if the input string is "babad," the function should return either "bab" or "aba" as both are valid palindromes of length 3 in the given input string.
In summary, the goal is to find the longest palindromic substring in the given string and handle cases where there might be multiple palindromes of the same length.


longestPalindrome Function:

public static String longestPalindrome(String s) {
    if (s == null || s.length() < 1) {
        return "";
    }
    
    int start = 0, end = 0;

    for (int i = 0; i < s.length(); i++) {
        int len1 = expandAroundCenter(s, i, i);
        int len2 = expandAroundCenter(s, i, i + 1);
        int len = Math.max(len1, len2);

        if (len > end - start) {
            start = i - (len - 1) / 2;
            end = i + len / 2;
        }
    }

    return s.substring(start, end + 1);
}

Description:
The longestPalindrome function takes a string s as input and returns the longest palindromic substring found in the input string.

It starts by checking if the input string is null or empty. If so, it returns an empty string as there cannot be a palindrome in an empty or null string.

The function uses a two-pointer approach, where start and end represent the indices of the longest palindromic substring found so far.

It iterates through each character in the input string, and for each character, it expands around the center to find the longest palindromic substring that includes the current character.

The lengths len1 and len2 are obtained by expanding around the center for both odd and even length palindromes.

The len is then calculated as the maximum of len1 and len2.

If the calculated length is greater than the length of the current longest palindromic substring (end - start), it updates the start and end indices to include the new palindrome.

Finally, it returns the substring from start to end + 1 as the longest palindromic substring.


