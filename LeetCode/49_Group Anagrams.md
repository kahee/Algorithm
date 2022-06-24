## 49. Group Anagrams
https://leetcode.com/problems/group-anagrams/

### 문제 풀이 
```python
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        result_dict = defaultdict(list)
        for s in strs:
            sorted_str = "".join(sorted(list(s)))
            result_dict[sorted_str].append(s)
        return result_dict.values()
```

- sorted(s) 로 해도 상관없음 
