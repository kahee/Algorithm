## 5. Longest Palindromic Substring
https://leetcode.com/problems/longest-palindromic-substring/

### 문제 풀이 
- Palindromic 이란? 
    팰린드롬은 거꾸로 읽어도 제대로 읽는 것과 같은 문장이나 낱말, 숫자, 문자열
- 시작과 끝 지점의 인덱스를 시작 지점으로 잡고 문자 같은지 확인 

```python 
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s) <= 1:
            return s

        i,l=0,0
        for j in range(len(s)):
            if s[j-l: j+1] == s[j-l: j+1][::-1]:
                i, l = j-l, l+1
            elif j-l > 0 and s[j-l-1: j+1] == s[j-l-1: j+1][::-1]:
                i, l = j-l-1, l+2
        return s[i: i+l]
```


### 참고 
https://hyerios.tistory.com/191