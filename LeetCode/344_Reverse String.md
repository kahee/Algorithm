## 344. Reverse String
https://leetcode.com/problems/reverse-string/

### 문제풀이 

```python 
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        string_length = len(s)
        for i in range(string_length//2):
            index = string_length - i - 1
            temp = s[i]
            s[i] = s[index]
            s[index] = temp
        return 
```

### 책에서 제안한 방식
```python 
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        left, right = 0, len(s) - 1
        while left < right:
            s[left], s[right] = s[right], s[left]
            left += 1
            right -= 1
        return 
```
- 투포인터 방식 

```python 
 def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        s[::] = s[::-1]
        return 
```
- 처음에 s[::-1] 이렇게 했는데 왜 안되지 했는데 `the input array in-place with O(1) extra memory.` 제약 조건이 있었다.. 공간 복잡도 O(1)
- 실행시간이나 메모리방식에서는 크게 차이는 없는듯 
- s[::] deepcopy 와 비슷함 