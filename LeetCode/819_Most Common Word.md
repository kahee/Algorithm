## 819. Most Common Word
https://leetcode.com/problems/most-common-word/

### 문제풀이 

```python 
import re

class Solution:
    def mostCommonWord(self, paragraph: str, banned: List[str]) -> str:
        split_list =  re.sub(r"[!?',;.]"," ",paragraph.lower()).split()
        split_list = [word for word in split_list if word not in banned]
        most_common_word = collections.Counter(split_list).most_common(1)
        
        return most_common_word[0][0]
```

- 문제에서는 , (콤마) 다음에 뭔가가 없었던것 같은데.. 왜!!!!! bbbc 이게 틀리다고 하는지 이해가 안간다
- "a, a, a, a, b,b,b,c, c" ["a"] -> 이거때문에 split 할때 " " 이부분을 삭제함

### 해결 풀이 
- 내 풀이랑 달랐던 부분은 정규표현식정도 `[^\w]`  