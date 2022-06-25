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

```python 
class Solution:
    def longestPalindrome(self, s: str) -> str:
        # 팰린드롬 판별 및 투 포인터 확장
        def expand(left: int, right: int) -> str: 
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[left + 1:right]
        
        # 해당 사항이 없을 대 빠르게 리턴
        if len(s) < 2 or s == s[::-1]:
            return s
        
        result = ''
        
        # 슬라이딩 윈도우 우측으로 이동
        for i in range(len(s) - 1):
            result = max(result,
                            expand(i, i + 1),
                            expand(i, i + 2),
                            key = len)
        return result     
```
- 책에서 제안한 방법은 위와 같은 방법인데, expand(i, i+1) = 짝수, expand(i, i+2) = 홀수 인 상황이다. 

### 내가 푼 틀린방법 
```python 
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s) % 2 != 0:
            start_index = len(s)//2 + 1
            is_even = True
        else:
            start_index = len(s)//2
            is_even = False

        result = None
        for i in range(len(s)-start_index):
            if i == 0:
                i = start_index

            print(i)
            print(start_index)
            if not is_even:
                if(s[i-1] == s[i+1]):
                    
                    result = s[i:i+2]
            else:
                if(s[i-1] == s[i+1]):
                    result = s[i-1:i+2]
                    
        return result

# 두번째 방법
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def expand(left: int, right: int) -> str: 
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[left + 1:right]
        
        if len(s) < 2 or s == s[::-1]:
            return s
        
        result = ''
        for i in range(len(s)-1):
            if len(s)% 2 != 0:
                result = max(result, expand(i,i+2), key=len)
            else:
                result = max(result, expand(i,i+1), key=len)
        
        return result
```
- 내가 처음에 판별했던 방법의 경우에는 홀수 짝수 나눠서 진행하게 했는데 이렇게 접근한게 문제였을까..?
- ac 테스트 케이스 통과를 못하는데 .. 나처럼 이해못하는 사람들이 좀있었던것 같다.. (https://leetcode.com/problems/longest-palindromic-substring/discuss/1984790/how-can-%22ac%22-long-term-palindromic-string-will-be-%22a%22.-Wrong-test-case-in-leet-code)
    - 결과적으로 둘이 같지 않기 때문에 a, c 둘중에 하나라도 나와야한다는거고 내 접근방법으로 하는 경우 짝수이기 때문에 없다.  


### 참고 
https://hyerios.tistory.com/191