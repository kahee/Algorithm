## 125. Valid Palindrome
https://leetcode.com/problems/valid-palindrome/

### 문제풀이 

```python
import re

class Solution:
    def isPalindrome(self, s: str) -> bool:
        
        new_s = re.sub(r"[^a-zA-Z0-9]","",s)
        if len(new_s) == 0:
            return True
        
        lower_s = new_s.lower()
        reversed_str = lower_s[::-1]
        return reversed_str == lower_s
        
```

### 책에서 제안한 방방
```python

class Solution:
    def isPalindrome(self, s: str) -> bool:

        strs = []
        for char in s:
            if char.isalnum():
                strs.append(char.lower())
        
        while len(strs) > 1:
            if strs.pop(0) != strs.pop():
                return False
        
        return True
        
```

내가 푼 방법이 좀더 빠르고, 저장공간을 덜 사용하게 되어있음 

### 좀더 나은 방법

```python 
    def isPalindrome(self, s: str) -> bool:
        s = re.sub(r'[^a-zA-Z0-9]','',s).lower()
        return s == s[::-1]
        
```