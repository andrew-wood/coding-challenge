# coding-challenge



# Single Character Search
Take an input of a string and find the first character which only appears once in the string.

# Fibonacci 
Implement a function fibonacci(int x) that returns the xth number in the fibonacci sequence. Must be order N time complexity and order 1 space complexity.

# Fibonacci Memoization
Calculate the nth fibonacci number recursively using memoization in javascript observing closure.

# Pair Summing
Write a function that counts how many pairs of numbers in an array add up to a given number. To follow up: how to do this more efficiently.

# Letters of Alphabet
Implement a function to determine which letters of the alphabet were missing from an input string.

# Run Length Encoding *
Given a string of characters return the run length encoded version. E.g. given the string “aabbbccddddaaa”, the return value would be “a2b3c2d4a3”.

# Longest Substring
Write a function that takes a string and returns the longest substring in that string made up of the same character and the index the substring starts on, e.g. given the string “aabbbccddddaaa” the substring is “dddd” starting at index 7.

# Second Lowest Number
Write a function that takes an array of numbers and returns the second lowest number in the array, or zero if the length of the array is less than two.

# Powers of 10
Given a number x, write a function to determine if this is a power of 10. 

# Median of Two Arrays
Given two sorted int arrays find the median element.

# Sums of Consecutive Array Elements
Given an array of non-negative integers and a target integer, find the length of the shortest continuous subsequence such that the sum is greater than the target.

# Binary Search Tree
Build a binary search tree from an array of numbers, given a BST class with a Node, and a Node class with a value, a left Node and a right Node. Then fix a traversal method, so that it does In-Order Traversal.

# Prime Factorisation
Factorise a given number, expressing the result as an int[] of primes. e.g. 6 = [2,3] and 12 = [2,2,3]

# Longest Anagram from Dictionary 
Given an array of words, find all the longest anagrams of the supplied letters. E.g. Dictionary = [“toe”, “toes”, “got”, “toga”, “other”], letters_1 = “otge”, result_1 = [“toe”, “got”],  letters_2 = “otes”, result_2 = [“toes”]. What if performance is important - e.g. the dictionary contains many thousands of words?

# Hash Map
Implement a MyHashMap class, which contained generic methods ‘put(K,V)’ and ‘get(K)’ which would perform in constant time. 

# Anagram Sets
Given a List of words, return a set of set of words where each word in an inner set is an anagram of every other word in the set.
Eg - given [“cat”, “dog”, “god”, “cat”] return [[“cat”], [“dog”, “god”]].

# Prime Countdown Generator
Use a generator function to yield the primes down from n.
E.g. function* countdownPrimes (n)
Further points for tests and outputing the results as a single array afterwards.

# Longest Common Subsequence
Given two sequences, find the length of longest subsequence present in both of them. A subsequence is a sequence that appears in the same relative order, but not necessarily contiguous. For example, “abc”, “abg”, “bdf”, “aeg”, ‘”acefg”, .. etc are subsequences of “abcdefg”. So a string of length n has 2^n different possible subsequences.
Solution see https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/

# Word Search
Calculate the word that occurs most frequently in a block of text passed as a String[].  Where the word contains two or more vowels.
As a follow up if there are multiple words with the same number of occurrences return the one that occurred first in the array.
Triple Step:
A Child is running up a staircase with n steps and can hop either 1 step, 2 steps, or 3 steps at a time. Implement a method to count how many possible ways the child can run up the stairs
Solution see https://www.geeksforgeeks.org/count-ways-reach-nth-stair-using-step-1-2-3/ and https://github.com/wzhishen/cracking-the-coding-interview/blob/master/src/chap09/Q01.java

# Robot Movement
Given a string like “UDDLR” which corresponds to robot movements calculate the robots end coordinates when it starts at [0, 0]. Ignore all other characters given (“2xUP” would just move the robot up one) and the robot can move into negative coordinates.

# Merge Overlapping Intervals
Given a set of time intervals in any order, merge all overlapping intervals into one and output the result which should have only mutually exclusive intervals. Let the intervals be represented as pairs of integers for simplicity. 
For example, let the given set of intervals be {{1,3}, {2,4}, {5,7}, {6,8} }. The intervals {1,3} and {2,4} overlap with each other, so they should be merged and become {1, 4}. Similarly {5, 7} and {6, 8} should be merged and become {5, 8}
Solution see https://www.geeksforgeeks.org/merging-intervals/

# Highest Average Score *
Find the highest student average score during their course.   If the average score is not an integer, then return floor.
Input:
String[][] scores = {
            	{“George”, “87”},
            	{“Charles”, 100},
            	{“Bob”, 64},
{“Charles”, 22}
}
Test case:
highestAvgScore(scores) == 87
