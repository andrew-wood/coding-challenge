# coding-challenge



# Single Character Search
Take an input of a string and find the first character which only appears once in the string.
	public class SingleCharacter {

		public static void main(String args[]) {
			System.out.println(findFirstSingleCharacter("bbccddeffgghhijjkkllemmnn"));
		}
	
		public static String findFirstSingleCharacter(String inputString) {
		
			for(int index=0;index<inputString.length();index++) {
				char current = inputString.charAt(index);
				if(inputString.indexOf(current) ==
						inputString.lastIndexOf(current)){
							return Character.toString(current);
						}
			}
		
			return "not found any";
		
		
		}
	}


# Fibonacci 
Implement a function fibonacci(int x) that returns the xth number in the fibonacci sequence. Must be order N time complexity and order 1 space complexity.
    public class Fibonacci {
	    public static void main(String args[]) {
		    System.out.println(calculateNthFib(9));
		    System.out.println(calculateNthFibRec(9));
	    }
	
	    public static int calculateNthFib(int x) {
		    int a = 1, b = 1, c =x;
		    if (x <= 0) {
			    return x;
		    }
		    for (int i = 2; i <= x; i++ ) {
			    c = a + b;
			    a = b;
			    b = c;
		    }
		    return b;
	    }
	
	    public static int calculateNthFibRec(int x) {
		    if(x < 1)
			    return 0;
		    else if(x == 1 || x ==2) {
			    return 1;
		    } else {
			    return calculateNthFibRec(x-1) + calculateNthFibRec(x-2);
		    }		
        }
	}


# Fibonacci Memoization
Calculate the nth fibonacci number recursively using memoization in javascript observing closure.

# Pair Summing
Write a function that counts how many pairs of numbers in an array add up to a given number. To follow up: how to do this more efficiently.

    public class PairSumming {

	    public static void main(String args[]) {
		    int[] numbers = {1,2,3,4,5,6,6,7,8,9};
		    int target = 12;
		    System.out.println(pairSumMatches(numbers, target)); //should be 3 3+9 4+8 5+7
	    }
	
	    public static int pairSumMatches(int[ ] arrayOfNums, int target) {
		    int matchesFound = 0;
		    for(int i = 0; i < arrayOfNums.length; i++) {
			    for(int j = 0; j < arrayOfNums.length; j++) {
				    if (i != j && (arrayOfNums[i]+arrayOfNums[j]==target)) {
					    matchesFound ++;
				    }
			    }
		    }
		//we will find it twice
		return matchesFound/2;
		
		//n-squared complexity
		// can improve - order array
		// find numbers less than target
	    }
    }


# Letters of Alphabet
Implement a function to determine which letters of the alphabet were missing from an input string.

    public class MissingLetters {

	    public static void main(String args[]) {
		    System.out.println(getMissingLetters("abcfghklmpqruvwz"));
	    }
	
	    public static String getMissingLetters(String inputString) {
		    StringBuilder sb = new StringBuilder();
		    for(int i=0;i<26;i++) {
			    char current = (char) ((char) 65 + i);
			    if((inputString.indexOf(65 + i)>-1) || (inputString.indexOf(97 + i)>-1)){
    				sb.append(current + ": found\n");
	    		} else {
		    		sb.append(current + ": not found\n");
			    }	
		}
		
		return sb.toString();
		
		
	    }
    }


# Run Length Encoding *
Given a string of characters return the run length encoded version. E.g. given the string “aabbbccddddaaa”, the return value would be “a2b3c2d4a3”.


    public class RunLengthEncoding {

	    public static void main(String args[]) {
		    System.out.println(runLengthEncoder("abcdefg"));
	    }
	
	
	    public static String runLengthEncoder(String inputString) {
		    StringBuilder sb = new StringBuilder();
		    char lastChar;
		    int currentLength = 0;
		
		    if(inputString.length()>0)
		    {
			    lastChar = inputString.charAt(0);
			    for(int i =0; i<inputString.length(); i++) {
				    if(lastChar == inputString.charAt(i)) {
					    currentLength = currentLength + 1;
				    } else {
					    if(currentLength > 0) {
						    sb.append(lastChar).append(currentLength);
					    }
					    lastChar = inputString.charAt(i);
					    currentLength = 1;
				    }
			    }
			    sb.append(lastChar).append(currentLength);
		    }	
		    return sb.toString();
	    }
    }


# Longest Substring
Write a function that takes a string and returns the longest substring in that string made up of the same character and the index the substring starts on, e.g. given the string “aabbbccddddaaa” the substring is “dddd” starting at index 7.


    public class LongestSubString {

	    public static void main(String args[]) {
		    System.out.println(findLongestSubString("abbbbbbceeeeeeeeeeeeeeeeffffffggg"));
	    }
	
	
	    public static String findLongestSubString(String inputString) {
		    char lastChar;
		    int currentLength = 0;
		    int currentStartIndex = 0;
		    int maxLength =0;
		    int maxStartIndex = 0;
		    if(inputString.length()>0)
		    {
			    lastChar = inputString.charAt(0);
			    for(int i =0; i<inputString.length(); i++) {
    				if(lastChar == inputString.charAt(i)) {
	    				currentLength = currentLength + 1;
		    			if(currentLength > maxLength) {
			    			maxLength = currentLength;
				    		maxStartIndex = currentStartIndex;
					    }
				    } else {
					    currentStartIndex = i;
					    lastChar = inputString.charAt(i);
					    currentLength = 1;
				    }
			    }
					
		    }
	
		    StringBuilder sb = new StringBuilder();
		    sb.append(inputString.substring(maxStartIndex, maxStartIndex+maxLength));
		    sb.append(" found, starting at index ");
		    sb.append(maxStartIndex);
		    return sb.toString();
	    }
    }


# Second Lowest Number
Write a function that takes an array of numbers and returns the second lowest number in the array, or zero if the length of the array is less than two.


    public class SecondLowestNumber {

	    public static void main(String args[]) {
		    int[] numbers = {7,12,1,5,6,14,5,7,92,9,1,12,18,22,33,13};
		    System.out.println(findSecondLowest(numbers));
	    }
	
	
	    public static int findSecondLowest(int[] numbers) {
		    int lowest = numbers[0];
		    int secondLowest = Integer.MAX_VALUE;
		    if(numbers.length <=2) {
    			return 0;
	    	}
		    for (int i =0; i< numbers.length; i++) {
			    if(numbers[i]<lowest) {
    				lowest = numbers[i];
	    		}
		    	if(numbers[i] > lowest && numbers[i]<secondLowest) {
			    	secondLowest = numbers[i];				
			    }	
		    }
		    return secondLowest;
	    }
    }


# Powers of 10
Given a number x, write a function to determine if this is a power of 10. 


    public class PowersOfTen {

	    public static void main(String args[]) {
		    System.out.println(isAPowerOfTen(60));
		    System.out.println(isAPowerOfTen(10000000));
	    }
	    public static boolean isAPowerOfTen(int x) {
		    boolean isAPowerOfTen = false;
		    while(x>1) {
    			if(x%10 == 0) {
	    			x = x/10;
		    		if(x == 1) {
			    		isAPowerOfTen = true;
				    	break;
				    }
			    }
			    else {
				    break;
			    }
		    }
		    return isAPowerOfTen;
	    }
    }


# Median of Two Arrays
Given two sorted int arrays find the median element.

    public class Median2Arrays {
	    	public static void main(String args[]) {
		    	int[] a = {3,4,7,9,12,23,56,67,88,111,122,155,166};
			    int[] b = {4,73,89,99,121,122,155,212,213};
			    System.out.println(findMedianSortedArrays(a,b));
		    }
	        public static double findMedianSortedArrays(int[] input1, int[] input2) {
	            if(input1.length > input2.length) {
	    	    //we want the first array to be shorter as it will solve in Olog(min(m,n))
	    	    int[] temp = input2;
	    	    input2 = input1;
	    	    input1 = temp;
                }
	    	
	    	    int x = input1.length;
	            int y = input2.length;
	        
	            int low = 0;
	            int high = x;
	       
	            while (low <= high) {
	                int partitionX = (low + high)/2;
	                int partitionY = (x + y + 1)/2 - partitionX;
	            
	                int maxLeftX = (partitionX == 0) ? Integer.MIN_VALUE: input1[partitionX -1];
	                int minRightX = (partitionX == x) ? Integer.MAX_VALUE : input1[partitionX];
	            
	                int maxLeftY = (partitionY == 0) ?  Integer.MIN_VALUE: input2[partitionY -1];
	                int minRightY = (partitionY == y) ? Integer.MAX_VALUE: input2[partitionY];
	            
	                if(maxLeftX <= minRightY && maxLeftY <= minRightX) {
	            	//success
	            	    if((x+y) % 2 == 0) {
	            		    //even number of elements need to average the middle pair
	            		    return ((double)Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY))/2;
	            	    } else {
	            		    //odd numbers the extra element is on the left.
	            		    return (double)Math.max(maxLeftX, maxLeftY);
	            	    }
	                } else if (maxLeftX > minRightY) {
	            	    high = partitionX - 1;
	                } else {
	            	    low = partitionX + 1;
	                }
	            
	            }
	        
	            //probably unsorted arrays...
	            throw new IllegalArgumentException();
	        }
	    }


# Sums of Consecutive Array Elements
Given an array of non-negative integers and a target integer, find the length of the shortest continuous subsequence such that the sum is greater than the target.

    public class ShortestSubsequence {

	    public static void main(String args[]) {
		    int target = 21;
		    int[] a = {7,3,10,2,10};
		
		    System.out.println(findShortestSequence(target, a));
	    }
	
	    public static int findShortestSequence(int target, int[] a) {
		    boolean foundConseq;
		    int shortestFound = Integer.MAX_VALUE;
		    int count;
		    for(int i = 0; i< a.length; i++) {
    			foundConseq = false;
	    		int total = a[i]; 
		    	count = 1;
			    do {
				    if(total > target) {
					    foundConseq = true;
				    }
				    else {
					    if(i+count < a.length) {
						    total = total + a[i+count];
						    count = count +1;
					    }
					    else {
						    break;
					    }
				    }
			    }
			    while(!foundConseq);
			    if((count < shortestFound) && foundConseq) {
				    shortestFound = count;
			    }
			
		    }
		    return shortestFound;
	    }
    }


# Binary Search Tree
Build a binary search tree from an array of numbers, given a BST class with a Node, and a Node class with a value, a left Node and a right Node. Then fix a traversal method, so that it does In-Order Traversal.



    public class BT {
	    Node root;
	    class Node{
		    private Node left;
		    private Node right;
		    private int value;
		
		    public Node(int item) {
			    value = item;
			    left =null;
			    right = null;
		    }
		
		    public void insertLeft(Node node) {
			    this.left = node;
		    }
		    public void insertRight(Node node) {
			    this.right = node;
		    }
		    public void traverse() {
			    if(left!=null)
    				left.traverse();
	    		System.out.println(this.value);
			    if(right!=null)
				    right.traverse();
		    }
		    public int getValue() {
			    return value;
		    }
		    public void insertNode(Node node) {
			    if(node.getValue() < value) {
    				if(left == null) {
	    				insertLeft(node);
		    		} else {
			    		left.insertNode(node);
				    }
			    } else {
				    if(right ==null) {
					    insertRight(node);
				    } else {
					    right.insertNode(node);
				    }
				
			    }
		    }
	    }
	
	
	    public static void main(String args[]) {
		    int[] values = {4,3,6,3,7,2,8,3,4,6,3};
		    BT root = new BT();
		    root.root = root.new Node(4);
		    for(int i=1; i<values.length; i++) {
			    BT.Node n = root.new Node(values[i]);
			    root.root.insertNode(n);
		    }
		
		    root.root.traverse();
	    }
	
	
    }


# Prime Factorisation
Factorise a given number, expressing the result as an int[] of primes. e.g. 6 = [2,3] and 12 = [2,2,3]

    import java.util.ArrayList;
    import java.util.List;

    public class PrimeFactorization {

	    public static void main(String args[]) {
		    int number = 2796707;
		    List<Integer> factors = factorise(number);
		    for(Integer factor: factors) {
			    System.out.println(factor);
		    }
	    }
	    public static boolean isAFactor(int number, int candidate) {
		    return number%candidate == 0;
	    }
	
	
	    public static List<Integer> factorise(int n) {
		    List<Integer> factors = new ArrayList<Integer>();
		
		    for(int i=2; i<=n; i++) {
			    while(n % i == 0) {
				    factors.add(i);
				    n= n/i;
				
			    }
		    }
		
		    return factors;
		
	    }
    }


# Longest Anagram from Dictionary 
Given an array of words, find all the longest anagrams of the supplied letters. E.g. Dictionary = [“toe”, “toes”, “got”, “toga”, “other”], letters_1 = “otge”, result_1 = [“toe”, “got”],  letters_2 = “otes”, result_2 = [“toes”]. What if performance is important - e.g. the dictionary contains many thousands of words?

# Hash Map
Implement a MyHashMap class, which contained generic methods ‘put(K,V)’ and ‘get(K)’ which would perform in constant time. 

# Anagram Sets
Given a List of words, return a set of set of words where each word in an inner set is an anagram of every other word in the set.
Eg - given [“cat”, “dog”, “god”, “cat”] return [[“cat”], [“dog”, “god”]].

    import java.util.ArrayList;
    import java.util.Arrays;
    import java.util.HashMap;
    import java.util.List;
    import java.util.Map;

    public class AnagramSets {

	    public static void main(String args[]) {
		    String[] words = {"cat","dog","god"};
		    findAnagramSets(words);
	    }
	
	    public static List<List<String>> findAnagramSets(String[] words){
		    List<List<String>> groups = new ArrayList<>();
		    HashMap<String, List<String>> map = new HashMap<>();
		    for(String word: words) {
    			char[] letters = word.toCharArray();
	    		Arrays.sort(letters);
		    	String sorted = new String(letters);
			    if(!map.containsKey(sorted)) {
				    map.put(sorted, new ArrayList<>());
			    }
			    map.get(sorted).add(word);
		    }
		    groups.addAll(map.values());
		
		    return groups;
	    }
	
    }


# Prime Countdown Generator
Use a generator function to yield the primes down from n.
E.g. function* countdownPrimes (n)
Further points for tests and outputing the results as a single array afterwards.

    import java.util.ArrayList;
    import java.util.List;
    import java.util.Collections;
    public class PrimeCountdown {

	
	    public static void main(String args[]) {
		    List<Integer> primes = getCountdownPrimes(3000);
		    for(int i: primes) {
			    System.out.println(i);
		    }
	    }
	
	    public static boolean isPrime(int n, List<Integer> primes) {
		    int start =2;
		    if(primes.size() >0) {
			    for(int prime: primes) {
				    if(n%prime==0) {
					    start = prime;
					    return false;
				    }
			    }
		    }
		    for(int i =start; i<n; i++) {
			    if(n%i==0) {
				    return false;
			    }
		    }
		    return true;
	    }
	
	    public static List<Integer> getCountdownPrimes(int n) {
		    List<Integer> primes = new ArrayList<Integer>();
		    for(int i = 2; i<=n; i++) {
			    if(isPrime(i, primes)) {
				    primes.add(i);
			    }
		    }
		    Collections.reverse(primes);
		    return primes;
		
	    }
    }


# Longest Common Subsequence
Given two sequences, find the length of longest subsequence present in both of them. A subsequence is a sequence that appears in the same relative order, but not necessarily contiguous. For example, “abc”, “abg”, “bdf”, “aeg”, ‘”acefg”, .. etc are subsequences of “abcdefg”. So a string of length n has 2^n different possible subsequences.
Solution see https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/


    public class LongestCommonSubsequence {
	
        public static int findLongestCommonSubsequence(char str1[],char str2[]){
            //2d array 1 bigger than the size of the strings - all values will be zero
            int temp[][] = new int[str1.length + 1][str2.length + 1];
            int max = 0;
            for(int i=1; i < temp.length; i++){
                for(int j=1; j < temp[i].length; j++){
                    if(str1[i-1] == str2[j-1]) {
                	    //found a match - add 1 to diagonal up-left
                        temp[i][j] = temp[i - 1][j - 1] + 1;
                    }
                    else
                    {
                	    //not match max of above or left
                        temp[i][j] = Math.max(temp[i][j-1],temp[i-1][j]);
                    }
                    if(temp[i][j] > max){
                        max = temp[i][j];
                    }
                }
            }
            return max;        
        }
    
    
        public static void main(String args[]){
            String str1 = "ABCDE";
            String str2 = "AEBD";
        
            int result = findLongestCommonSubsequence(str1.toCharArray(), str2.toCharArray());
            System.out.print(result);
        }
    
    }


# Word Search
Calculate the word that occurs most frequently in a block of text passed as a String[].  Where the word contains two or more vowels.
As a follow up if there are multiple words with the same number of occurrences return the one that occurred first in the array.

	import java.util.HashMap;
	import java.util.Map;

	public class WordSearch {

		public static void main(String args[]) {
			String[] words = {"The", "most", "potential", "football", "football", "potential", "potential"};
		
			System.out.println(mostFrequentWord(words));
		}
	
		public static String mostFrequentWord(String[] words) {
			Map<String, Integer> wordCount = new HashMap<String, Integer>();
			for(int i = 0; i< words.length; i++) {
				if(contains2OrMoreVowels(words[i])){
					if(wordCount.containsKey(words[i])) {
						int count = wordCount.get(words[i]) +1;
						wordCount.replace(words[i], count);
					}
					else {
						wordCount.put(words[i], 1);
					}
				
				}
			}
		
			int most = 0;
			String mostWord = "";
			for(String word: wordCount.keySet()) {
				int count = wordCount.get(word);
				if(count > most) {
					most = count;
					mostWord = word;
				}

			}

			return mostWord;
		}

		public static boolean contains2OrMoreVowels(String word) {
			char[] letters = word.toCharArray();
			boolean isAWord = false;
			int vowelCount = 0;
			char[] vowels = {'A','a','E','e','I','i','O','o','U','u'};
			for(int i=0; i< letters.length; i++) {
				for(int j=0; j< vowels.length; j++) {
					if(letters[i]==vowels[j]) {
						vowelCount++;
						break;
					}
				}
				if(vowelCount >=2) {
					isAWord=true;
					break;
				}
			}
			return isAWord;
		}

	}



# Triple Step
A Child is running up a staircase with n steps and can hop either 1 step, 2 steps, or 3 steps at a time. Implement a method to count how many possible ways the child can run up the stairs
Solution see https://www.geeksforgeeks.org/count-ways-reach-nth-stair-using-step-1-2-3/ and https://github.com/wzhishen/cracking-the-coding-interview/blob/master/src/chap09/Q01.java


    public class CountSteps {
	    public static int countWays(int n) { 
	        int[] res = new int[n + 1]; 
	        res[0] = 1; 
	        res[1] = 1; 
	        res[2] = 2; 
	  
	        for (int i = 3; i <= n; i++) 
	            res[i] = res[i - 1] + res[i - 2] 
	                                + res[i - 3]; 
	  
	        return res[n]; 
	    } 
	  
	    public static void main(String argc[]) 
	    { 
	        int n = 4; 
	        System.out.println(countWays(n)); 
	    } 
    }


# Robot Movement
Given a string like “UDDLR” which corresponds to robot movements calculate the robots end coordinates when it starts at [0, 0]. Ignore all other characters given (“2xUP” would just move the robot up one) and the robot can move into negative coordinates.

    public class RobotMovement {

	    public static void main(String[] args) {
		    // TODO Auto-generated method stub
		
		    String input1  = "UDDLR";
		    int[] coords = getCoordinates(input1);
	    }
	
	
	    public static int[] getCoordinates(String movementString) {
		    int[] coords = {0,0};
		
		    char[] moves = movementString.toCharArray();
		
		    for(int i=0; i<moves.length; i++) {
			    switch(moves[i]) {
			    case 'U':
				    coords[1] = coords[1] +1;
				    break;
			    case 'D':
				    coords[1] = coords[1] -1;
				    break;
			    case 'L':
				    coords[0] = coords[0] -1;
				    break;
			    case 'R':
				    coords[0] = coords[0] +1;
			}
		}		
		return coords;
		
	    }
	

    }


# Merge Overlapping Intervals
Given a set of time intervals in any order, merge all overlapping intervals into one and output the result which should have only mutually exclusive intervals. Let the intervals be represented as pairs of integers for simplicity. 
For example, let the given set of intervals be {{1,3}, {2,4}, {5,7}, {6,8} }. The intervals {1,3} and {2,4} overlap with each other, so they should be merged and become {1, 4}. Similarly {5, 7} and {6, 8} should be merged and become {5, 8}
Solution see https://www.geeksforgeeks.org/merging-intervals/

    import java.util.ArrayList;
    import java.util.Arrays;
    import java.util.List;

    public class MergeOverlapIntervals {
	    public static void main(String argsp[]) {
		    int[][] intervals = {{2,6},{7,10},{12,23},{1,3}};
		    int [][] newIntervals = merge(intervals);
		    System.out.println(newIntervals);
	    }
	
	    public static int[][] merge(int[][] intervals){
		    if(intervals.length <=1) {
			    return intervals;
		    }
		
		    Arrays.sort(intervals,(arr1, arr2) -> Integer.compare(arr1[0], arr2[0]));
		    List<int[]> outputArr = new ArrayList<int[]>();
		    int[] currentInterval = intervals[0];
		    outputArr.add(currentInterval);
		
		
		    for(int[] interval: intervals) {
			    int end = currentInterval[1];
			    int nStart = interval[0];
			    int nEnd = interval[1];
			
			    if(nStart < end) {
				    currentInterval[1] = nEnd;
			    } else {
				    outputArr.add(interval);
			    }
			
		    }
		    return outputArr.toArray(new int[outputArr.size()][]);
	    }
    }




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
