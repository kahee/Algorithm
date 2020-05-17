## First bad version
https://leetcode.com/problems/first-bad-version/

### 문제 풀이 

```python
# The isBadVersion API is already defined for you.
# @param version, an integer
# @return a bool
# def isBadVersion(version):

class Solution:
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        left = 1
        right = n
        while (left < right):
            mid = left + ((right - left) // 2)
            if isBadVersion(mid):
                right = mid
            else:
                left = mid + 1
        
        return left
```

- 1 부터 입력받은 version 까지는 순서대로 이미 정렬되어있다고 가정하고 binary search 방법을 이용 -> Binary Search 는 오름차순으로 정렬된 리스트에서 특정값의 위치를 찾는 알고리즘
- 이진탐색의 경우 오버플로우 버그가 있어서 `mid = left + right // 2`이렇게 하는 경우 오버플로우가 발생할 수 있기 때문에 `left + ((right - left) // 2)` 로 계산
- Specifically, it fails if the sum of low and high is greater than the maximum positive int value (231 - 1). The sum overflows to a negative value, and the value stays negative when divided by two.
- https://stackoverflow.com/questions/6735259/calculating-mid-in-binary-search

### 오답

1. 시간 초과

```python
# The isBadVersion API is already defined for you.
# @param version, an integer
# @return a bool
# def isBadVersion(version):

class Solution:
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        cur_version = n
        is_bad_version = True
        while is_bad_version != False:
            is_bad_version = isBadVersion(cur_version)
            if is_bad_version:
                cur_version -= 1
        first_bad_version = cur_version + 1
        return first_bad_version
 
```

- 이렇게 하는 경우 O(N) 