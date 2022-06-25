## 1. Two Sum
https://leetcode.com/problems/two-sum/

### 문제 풀이 
```python 
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums) -1):
            for j in range(i + 1, len(nums)):
                if (nums[i] + nums[j]) == target:
                    return [i, j]

```
- 내가 한 방식의 경우 O(n^2)
- 브루트 포스 방식 = 배열 2번 반복하면서 모든 조합 더해서 일일이 확인해보는 방식..

### 책에서 제안한 방식
```python 
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i, n in enumerate(nums):
            complement = target - n 
            
            if complement in nums[i+1:]:
                return [nums.index(n), nums[i+1:].index(complement) + (i +1)]
```
- O(n) 

```python 
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_map = {}
        for i, num in enumerate(nums):
            nums_map[num] = i
        
        for i, num in enumerate(nums):
            if target - num in nums_map and i != nums_map[target-num]:
                return [i, nums_map[target - num]]
```
- 평균적으로 O(1) 에 가능, 최악의 경우에는 O(n)
