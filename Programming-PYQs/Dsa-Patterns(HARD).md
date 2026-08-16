# DSA Patterns (HARD) - Python Solutions

All solutions converted to / kept in Python. Original problem descriptions preserved.

### 1. Two Sum – Arrays

Description: Find two indices such that their values sum to a target.

```python
def twoSum(nums, target):
    hashmap = {}
    for i, num in enumerate(nums):
        diff = target - num
        if diff in hashmap:
            return [hashmap[diff], i]
        hashmap[num] = i
    return []
```

### 2. Kadane’s Algorithm – Max Subarray Sum

Description: Find the maximum sum of a contiguous subarray.

```python
def maxSubArray(nums):
    max_sum = curr = nums[0]
    for num in nums[1:]:
        curr = max(num, curr + num)
        max_sum = max(max_sum, curr)
    return max_sum
```

### 3. Valid Anagram – Strings

Description: Check if two strings are anagrams.

```python
def isAnagram(s, t):
    return sorted(s) == sorted(t)
```

### 4. Longest Palindromic Substring – Strings

Description: Find the longest palindromic substring in a given string.

```python
def longestPalindrome(s):
    start = max_len = 0
    for i in range(len(s)):
        for l, r in [(i, i), (i, i + 1)]:
            while l >= 0 and r < len(s) and s[l] == s[r]:
                l -= 1
                r += 1
            if r - l - 1 > max_len:
                start = l + 1
                max_len = r - l - 1
    return s[start:start + max_len]
```

### 5. Reverse Linked List – Linked List

Description: Reverse a singly linked list.

```python
def reverseList(head):
    prev = None
    while head:
        nxt = head.next
        head.next = prev
        prev = head
        head = nxt
    return prev
```

### 6. Add Two Numbers – Linked List

Description: Add two numbers represented as linked lists.

```python
def addTwoNumbers(l1, l2):
    dummy = ListNode(0)
    curr = dummy
    carry = 0
    while l1 or l2 or carry:
        sum_val = (l1.val if l1 else 0) + (l2.val if l2 else 0) + carry
        carry = sum_val // 10
        curr.next = ListNode(sum_val % 10)
        curr = curr.next
        l1 = l1.next if l1 else None
        l2 = l2.next if l2 else None
    return dummy.next
```

### 7. Merge Intervals – Arrays

Description: Merge overlapping intervals.

```python
def merge(intervals):
    intervals.sort(key=lambda x: x[0])
    result = []
    for interval in intervals:
        if not result or result[-1][1] < interval[0]:
            result.append(interval)
        else:
            result[-1][1] = max(result[-1][1], interval[1])
    return result
```

### 8. Find Missing Number – Arrays

Description: Find the missing number in an array of 1 to N.

```python
def missingNumber(nums):
    n = len(nums)
    return n * (n + 1) // 2 - sum(nums)
```

### 9. Word Search – Backtracking

Description: Find if a word exists in a 2D grid of characters.

```python
def exist(board, word):
    for i in range(len(board)):
        for j in range(len(board[0])):
            if backtrack(board, word, i, j, 0):
                return True
    return False

def backtrack(board, word, i, j, index):
    if index == len(word):
        return True
    if i < 0 or j < 0 or i >= len(board) or j >= len(board[0]) or board[i][j] != word[index]:
        return False
    temp = board[i][j]
    board[i][j] = '#'
    found = (backtrack(board, word, i + 1, j, index + 1) or
             backtrack(board, word, i - 1, j, index + 1) or
             backtrack(board, word, i, j + 1, index + 1) or
             backtrack(board, word, i, j - 1, index + 1))
    board[i][j] = temp
    return found
```

### 10. Subsets – Backtracking

Description: Generate all possible subsets of a given set of numbers.

```python
def subsets(nums):
    result = []
    backtrack(nums, 0, [], result)
    return result

def backtrack(nums, start, current, result):
    result.append(list(current))
    for i in range(start, len(nums)):
        current.append(nums[i])
        backtrack(nums, i + 1, current, result)
        current.pop()
```

### 11. Find the Duplicate Number

Description: Find the duplicate number in an array containing n + 1 integers where each integer is between 1 and n.

```python
def findDuplicate(nums):
    slow = fast = nums[0]
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
    fast = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    return slow
```

### 12. Merge Sorted Array

Description: Merge two sorted arrays into one sorted array.

```python
def merge(nums1, m, nums2, n):
    i, j, k = m - 1, n - 1, m + n - 1
    while i >= 0 and j >= 0:
        if nums1[i] > nums2[j]:
            nums1[k] = nums1[i]
            i -= 1
        else:
            nums1[k] = nums2[j]
            j -= 1
        k -= 1
    while j >= 0:
        nums1[k] = nums2[j]
        j -= 1
        k -= 1
```

### 13. Rotate Image

Description: Rotate a given n x n 2D matrix by 90 degrees (clockwise).

```python
def rotate(matrix):
    n = len(matrix)
    for i in range(n // 2):
        for j in range(i, n - i - 1):
            temp = matrix[i][j]
            matrix[i][j] = matrix[n - j - 1][i]
            matrix[n - j - 1][i] = matrix[n - i - 1][n - j - 1]
            matrix[n - i - 1][n - j - 1] = matrix[j][n - i - 1]
            matrix[j][n - i - 1] = temp
```

### 14. Longest Substring Without Repeating Characters

Description: Find the length of the longest substring without repeating characters.

```python
def lengthOfLongestSubstring(s):
    char_set = set()
    left, max_len = 0, 0
    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        char_set.add(s[right])
        max_len = max(max_len, right - left + 1)
    return max_len
```

### 15. Container With Most Water

Description: Given an array of heights, find two lines that together with the x-axis form a container that holds the most water.

```python
def maxArea(height):
    left, right = 0, len(height) - 1
    max_area = 0
    while left < right:
        width = right - left
        min_height = min(height[left], height[right])
        max_area = max(max_area, width * min_height)
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    return max_area
```

### 16. Permutations

Description: Generate all permutations of a given list of numbers.

```python
def permute(nums):
    result = []
    backtrack(nums, [], result)
    return result

def backtrack(nums, current, result):
    if len(current) == len(nums):
        result.append(list(current))
        return
    for num in nums:
        if num in current:
            continue
        current.append(num)
        backtrack(nums, current, result)
        current.pop()
```

### 17. Set Matrix Zeroes

Description: Given an m x n matrix, if an element is 0, set its entire row and column to 0.

```python
def setZeroes(matrix):
    row_zero = any(matrix[i][0] == 0 for i in range(len(matrix)))
    col_zero = any(matrix[0][j] == 0 for j in range(len(matrix[0])))
    for i in range(1, len(matrix)):
        for j in range(1, len(matrix[0])):
            if matrix[i][j] == 0:
                matrix[i][0] = 0
                matrix[0][j] = 0
    for i in range(1, len(matrix)):
        for j in range(1, len(matrix[0])):
            if matrix[i][0] == 0 or matrix[0][j] == 0:
                matrix[i][j] = 0
    if row_zero:
        for i in range(len(matrix)):
            matrix[i][0] = 0
    if col_zero:
        for j in range(len(matrix[0])):
            matrix[0][j] = 0
```

### 18. Merge Intervals (Alternative)

Description: Given a collection of intervals, merge all overlapping intervals.

```python
def merge(intervals):
    if not intervals:
        return []
    intervals.sort(key=lambda x: x[0])
    merged = [intervals[0]]
    for interval in intervals[1:]:
        if merged[-1][1] >= interval[0]:
            merged[-1][1] = max(merged[-1][1], interval[1])
        else:
            merged.append(interval)
    return merged
```

### 19. Unique Paths II

Description: A robot is located at the top-left corner of a m x n grid, it can only move down or right, and some cells are blocked. Find how many unique paths the robot can take.

```python
def uniquePathsWithObstacles(grid):
    m, n = len(grid), len(grid[0])
    dp = [0] * n
    dp[0] = 1 if grid[0][0] == 0 else 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == 1:
                dp[j] = 0
            elif j > 0:
                dp[j] += dp[j - 1]
    return dp[-1]
```

### 20. Best Time to Buy and Sell Stock

Description: You are given an array where prices[i] is the price of a given stock on day i. Maximize profit by buying and selling once.

```python
def maxProfit(prices):
    min_price = float('inf')
    max_profit = 0
    for price in prices:
        min_price = min(min_price, price)
        max_profit = max(max_profit, price - min_price)
    return max_profit
```

### 21. Jump Game II

Description: Given an array of non-negative integers nums, return the minimum number of jumps to reach the last index.

```python
def jump(nums):
    jumps, current_end, farthest = 0, 0, 0
    for i in range(len(nums) - 1):
        farthest = max(farthest, i + nums[i])
        if i == current_end:
            jumps += 1
            current_end = farthest
    return jumps
```

### 22. Decode Ways

Description: A message containing letters from A-Z can be encoded into numbers. Determine the total number of ways to decode it.

```python
def numDecodings(s):
    if not s or s[0] == '0':
        return 0
    prev, curr = 1, 1
    for i in range(1, len(s)):
        temp = curr
        if s[i] == '0':
            curr = 0
        if s[i - 1] == '1' or (s[i - 1] == '2' and s[i] <= '6'):
            curr += prev
        prev = temp
    return curr
```

### 23. Word Break

Description: Given a non-empty string s and a dictionary of words wordDict, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

```python
def wordBreak(s, wordDict):
    wordSet = set(wordDict)
    dp = [False] * (len(s) + 1)
    dp[0] = True
    for i in range(1, len(s) + 1):
        for j in range(i):
            if dp[j] and s[j:i] in wordSet:
                dp[i] = True
                break
    return dp[len(s)]
```
