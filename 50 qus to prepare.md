

## **Arrays (15 Questions)**

1. **Two Sum** – \[LeetCode #1]
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        //put number, index in map - do this later
        //see if hashmap have target-num 
        //if yes then return index of number and target-num
        Map<Integer,Integer> map = new HashMap<>();
        for(int i=0;i<nums.length;i++)
        {
            if(map.containsKey(target-nums[i]))
            {
                return new int[]{i,map.get(target-nums[i])};
            }
            map.put(nums[i],i);
        }
        return null;
    }
}
```

2. **Best Time to Buy and Sell Stock** – \[#121]
3. **Contains Duplicate** – \[#217]
4. **Product of Array Except Self** – \[#238]
5. **Maximum Subarray (Kadane's Algorithm)** – \[#53]
6. **Majority Element** – \[#169]
7. **Move Zeroes** – \[#283]
8. **Rotate Array** – \[#189]
9. **Merge Sorted Array** – \[#88]
10. **Find Pivot Index** – \[#724]
11. **Subarray Sum Equals K** – \[#560]
12. **3Sum** – \[#15]
13. **4Sum** – \[#18]
14. **Insert Interval** – \[#57]
15. **Merge Intervals** – \[#56]

---

## **Strings (15 Questions)**

16. **Valid Anagram** – \[#242]
17. **Valid Palindrome** – \[#125]
18. **Longest Palindromic Substring** – \[#5]
19. **Longest Substring Without Repeating Characters** – \[#3]
20. **Minimum Window Substring** – \[#76]
21. **Longest Repeating Character Replacement** – \[#424]
22. **Group Anagrams** – \[#49]
23. **String Compression** – \[#443]
24. **Implement strStr() (Substring Search)** – \[#28]
25. **Repeated Substring Pattern** – \[#459]
26. **Valid Parentheses** – \[#20]
27. **Decode String** – \[#394]
28. **Longest Common Prefix** – \[#14]
29. **Multiply Strings** – \[#43]
30. **Roman to Integer** – \[#13]

---

## **HashMap / Hashing (10 Questions)**

31. **Two Sum** – \[#1] (Revisit for hashmap solution)
32. **Ransom Note** – \[#383]
33. **First Unique Character in a String** – \[#387]
34. **Word Pattern** – \[#290]
35. **Isomorphic Strings** – \[#205]
36. **Subarray Sum Equals K** – \[#560] (Key HashMap Problem)
37. **Longest Substring with At Most K Distinct Characters** – \[#340]
38. **Top K Frequent Elements** – \[#347]
39. **Happy Number** – \[#202]
40. **Design HashMap** – \[#706]

---

## **Frequently Asked / Mixed Concepts (10 Questions)**

41. **Valid Sudoku** – \[#36]
42. **Search in Rotated Sorted Array** – \[#33]
43. **Find Minimum in Rotated Sorted Array** – \[#153]
44. **Median of Two Sorted Arrays** – \[#4]
45. **Kth Largest Element in an Array** – \[#215]
46. **Sliding Window Maximum** – \[#239]
47. **Minimum Size Subarray Sum** – \[#209]
48. **Find All Anagrams in a String** – \[#438]
49. **Count and Say** – \[#38]
50. **LRU Cache** – \[#146]

---

### **How to Prepare for SDET Interviews with These:**

* Focus on **time & space complexity** analysis.
* Be able to write **clean, testable code** (unit tests for each function).
* Know how to debug edge cases (empty input, null values, large data sets).
* Be comfortable discussing **trade-offs between data structures** (e.g., HashMap vs. TreeMap).


