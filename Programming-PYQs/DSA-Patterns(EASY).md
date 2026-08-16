# 50 Coding Questions

## 1. Check Even or Odd

```python
n = int(input())
print("Even" if n % 2 == 0 else "Odd")
```

## 2. Check Prime Number

```python
import math
n = int(input())
prime = True
if n <= 1:
    prime = False
else:
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            prime = False
            break
print("Prime" if prime else "Not Prime")
```

## 3. Factorial of a Number

```python
n = int(input())
fact = 1
for i in range(1, n + 1):
    fact *= i
print(fact)
```

## 4. Fibonacci Series (First N Terms)

```python
n = int(input())
a, b = 0, 1
for i in range(n):
    print(a, end=" ")
    a, b = b, a + b
```

## 5. Reverse a Number

```python
n = int(input())
rev = 0
while n != 0:
    rev = rev * 10 + n % 10
    n //= 10
print(rev)
```

## 6. Check Palindrome Number

```python
n = int(input())
temp = n
rev = 0
while n != 0:
    rev = rev * 10 + n % 10
    n //= 10
print("Palindrome" if temp == rev else "Not Palindrome")
```

## 7. Armstrong Number

```python
n = int(input())
temp = n
sum_val = 0
while n != 0:
    digit = n % 10
    sum_val += digit ** 3
    n //= 10
print("Armstrong" if temp == sum_val else "Not Armstrong")
```

## 8. Sum of Digits

```python
n = int(input())
sum_val = 0
while n != 0:
    sum_val += n % 10
    n //= 10
print(sum_val)
```

## 9. Largest of Three Numbers

```python
a = int(input())
b = int(input())
c = int(input())
print(max(a, b, c))
```

## 10. GCD of Two Numbers

```python
a = int(input())
b = int(input())
while b != 0:
    a, b = b, a % b
print(a)
```

## 11. LCM of Two Numbers

```python
a = int(input())
b = int(input())
x, y = a, b
while y != 0:
    x, y = y, x % y
gcd = x
lcm = (a * b) // gcd
print(lcm)
```

## 12. Check Leap Year

```python
year = int(input())
if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
    print("Leap Year")
else:
    print("Not Leap Year")
```

## 13. Count Vowels and Consonants

```python
str_input = input().lower()
vowels = consonants = 0
for ch in str_input:
    if ch.isalpha():
        if ch in "aeiou":
            vowels += 1
        else:
            consonants += 1
print("Vowels:", vowels)
print("Consonants:", consonants)
```

## 14. Reverse a String

```python
str_input = input()
rev = ""
for i in range(len(str_input) - 1, -1, -1):
    rev += str_input[i]
print(rev)
```

## 15. Check Anagram

```python
s1 = input()
s2 = input()
print("Anagram" if sorted(s1) == sorted(s2) else "Not Anagram")
```

## 16. Remove Duplicates from String

```python
str_input = input()
result = ""
for ch in str_input:
    if ch not in result:
        result += ch
print(result)
```

## 17. Find Second Largest in Array

```python
n = int(input())
arr = list(map(int, input().split()))
first = second = float('-inf')
for num in arr:
    if num > first:
        second = first
        first = num
    elif num > second and num != first:
        second = num
print(second)
```

## 18. Linear Search

```python
n = int(input())
arr = list(map(int, input().split()))
key = int(input())
found = False
for num in arr:
    if num == key:
        found = True
        break
print("Found" if found else "Not Found")
```

## 19. Binary Search (Sorted Array)

```python
n = int(input())
arr = list(map(int, input().split()))
key = int(input())
low, high = 0, n - 1
found = False
while low <= high:
    mid = (low + high) // 2
    if arr[mid] == key:
        found = True
        break
    elif arr[mid] < key:
        low = mid + 1
    else:
        high = mid - 1
print("Found" if found else "Not Found")
```

## 20. Bubble Sort

```python
n = int(input())
arr = list(map(int, input().split()))
for i in range(n - 1):
    for j in range(n - i - 1):
        if arr[j] > arr[j + 1]:
            arr[j], arr[j + 1] = arr[j + 1], arr[j]
print(*arr)
```

## 21. Selection Sort

```python
n = int(input())
arr = list(map(int, input().split()))
for i in range(n - 1):
    min_index = i
    for j in range(i + 1, n):
        if arr[j] < arr[min_index]:
            min_index = j
    arr[i], arr[min_index] = arr[min_index], arr[i]
print(*arr)
```

## 22. Insertion Sort

```python
n = int(input())
arr = list(map(int, input().split()))
for i in range(1, n):
    key = arr[i]
    j = i - 1
    while j >= 0 and arr[j] > key:
        arr[j + 1] = arr[j]
        j -= 1
    arr[j + 1] = key
print(*arr)
```

## 23. Matrix Addition

```python
r, c = map(int, input().split())
a = [list(map(int, input().split())) for _ in range(r)]
b = [list(map(int, input().split())) for _ in range(r)]
for i in range(r):
    row = []
    for j in range(c):
        row.append(a[i][j] + b[i][j])
    print(*row)
```

## 24. Transpose of Matrix

```python
r, c = map(int, input().split())
a = [list(map(int, input().split())) for _ in range(r)]
for j in range(c):
    for i in range(r):
        print(a[i][j], end=" ")
    print()
```

## 25. Count Frequency of Element in Array

```python
n = int(input())
arr = list(map(int, input().split()))
key = int(input())
count = arr.count(key)
print(count)
```

## 26. Check if Array is Sorted

```python
n = int(input())
arr = list(map(int, input().split()))
sorted_flag = True
for i in range(n - 1):
    if arr[i] > arr[i + 1]:
        sorted_flag = False
        break
print("Sorted" if sorted_flag else "Not Sorted")
```

## 27. Merge Two Arrays

```python
n1 = int(input())
a = list(map(int, input().split()))
n2 = int(input())
b = list(map(int, input().split()))
merged = a + b
print(*merged)
```

## 28. Find Missing Number (1 to N)

```python
n = int(input())
arr = list(map(int, input().split()))
total = n * (n + 1) // 2
print(total - sum(arr))
```

## 29. Count Words in a String

```python
str_input = input().strip()
if not str_input:
    print(0)
else:
    print(len(str_input.split()))
```

## 30. Remove All Spaces from String

```python
str_input = input()
print(str_input.replace(" ", ""))
```

## 31. Find Duplicate Elements in Array

```python
n = int(input())
arr = list(map(int, input().split()))
seen = set()
duplicates = set()
for num in arr:
    if num in seen:
        duplicates.add(num)
    else:
        seen.add(num)
print(*duplicates)
```

## 32. Move All Zeros to End

```python
n = int(input())
arr = list(map(int, input().split()))
index = 0
for i in range(n):
    if arr[i] != 0:
        arr[index] = arr[i]
        index += 1
while index < n:
    arr[index] = 0
    index += 1
print(*arr)
```

## 33. Rotate Array Right by 1 Position

```python
n = int(input())
arr = list(map(int, input().split()))
last = arr[-1]
for i in range(n - 1, 0, -1):
    arr[i] = arr[i - 1]
arr[0] = last
print(*arr)
```

## 34. Check Palindrome String

```python
str_input = input()
rev = str_input[::-1]
print("Palindrome" if str_input == rev else "Not Palindrome")
```

## 35. Count Number of Digits

```python
n = int(input())
count = 0
while n != 0:
    n //= 10
    count += 1
print(count)
```

## 36. Sum of Elements in Array

```python
n = int(input())
arr = list(map(int, input().split()))
print(sum(arr))
```

## 37. Find Minimum Element in Array

```python
n = int(input())
arr = list(map(int, input().split()))
print(min(arr))
```

## 38. Pattern Printing (Right Triangle)

Input: 4  
Output:  
*  
**  
***  
****

```python
n = int(input())
for i in range(1, n + 1):
    print("*" * i)
```

## 39. Power of a Number

```python
base = int(input())
exp = int(input())
result = 1
for i in range(exp):
    result *= base
print(result)
```

## 40. Decimal to Binary

```python
n = int(input())
binary = ""
while n > 0:
    binary = str(n % 2) + binary
    n //= 2
print(binary)
```

## 41. Binary to Decimal

```python
binary = input()
decimal = 0
power = 0
for i in range(len(binary) - 1, -1, -1):
    if binary[i] == '1':
        decimal += 2 ** power
    power += 1
print(decimal)
```

## 42. Check Perfect Number

```python
n = int(input())
sum_val = 0
for i in range(1, n // 2 + 1):
    if n % i == 0:
        sum_val += i
print("Perfect" if sum_val == n else "Not Perfect")
```

## 43. Strong Number

```python
def factorial(n):
    fact = 1
    for i in range(1, n + 1):
        fact *= i
    return fact

n = int(input())
temp = n
sum_val = 0
while n != 0:
    digit = n % 10
    sum_val += factorial(digit)
    n //= 10
print("Strong" if temp == sum_val else "Not Strong")
```

## 44. Count Even and Odd Numbers in Array

```python
n = int(input())
arr = list(map(int, input().split()))
even = odd = 0
for num in arr:
    if num % 2 == 0:
        even += 1
    else:
        odd += 1
print("Even:", even)
print("Odd:", odd)
```

## 45. Find Intersection of Two Arrays

```python
n1 = int(input())
a = list(map(int, input().split()))
n2 = int(input())
b = list(map(int, input().split()))
for num in a:
    if num in b:
        print(num, end=" ")
```

## 46. Check Substring

```python
str_input = input()
sub = input()
if sub in str_input:
    print("Substring Present")
else:
    print("Substring Not Present")
```

## 47. Remove Specific Character from String

```python
str_input = input()
ch = input()[0]
print(str_input.replace(ch, ""))
```

## 48. Sum of Prime Numbers up to N

```python
import math
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True

n = int(input())
sum_val = 0
for i in range(2, n + 1):
    if is_prime(i):
        sum_val += i
print(sum_val)
```

## 49. Reverse Words in a Sentence

```python
str_input = input()
words = str_input.split()
print(*words[::-1])
```

## 50. Two Sum Problem

```python
n = int(input())
arr = list(map(int, input().split()))
target = int(input())
found = False
for i in range(n):
    for j in range(i + 1, n):
        if arr[i] + arr[j] == target:
            print(i, j)
            found = True
            break
    if found:
        break
if not found:
    print("No Pair Found")
```
