## 완주하지 못한 선수들
https://programmers.co.kr/learn/courses/30/lessons/42576

### 문제 풀이 

```python 
from collections import defaultdict
def solution(participant, completion):
    completion_dict = defaultdict(int)
    
    for name in completion:
        completion_dict[name] += 1
    
    for name in participant:
        if not completion_dict.get(name) :
            return name 
        elif completion_dict[name] == 0:
            return name
        elif completion_dict.get(name):
            completion_dict[name] -= 1
```

### 다른 사람 풀이
- collections.Counter: A Counter is a dict subclass for counting hashable objects. It is an unordered collection where elements are stored as dictionary keys and their counts are stored as dictionary values. Counts are allowed to be any integer value including zero or negative counts. The Counter class is similar to bags or multisets in other languages.
- Counter 를 이용하여 덧셈, 뺄셈, 교집합, 합집합 연산이 가능함

```python 
import collections

def solution(participant, completion):
    answer = collections.Counter(participant) - collections.Counter(completion)
    return list(answer.keys())[0]
```