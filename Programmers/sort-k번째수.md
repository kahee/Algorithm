## K 번째수
https://programmers.co.kr/learn/courses/30/lessons/42748

### 문제풀이 
- `sort()` 메소드는 리스트를 정렬된 상태로 변경 
- `sorted()`라는 내장 함수는 기존의 리스트를 변경하는 것이 아니라 정렬된 새로운 리스트를 반환

```python 
import copy 

def solution(array, commands):
    answer = []
    
    for n in range(len(commands)):
        i = commands[n][0]
        j = commands[n][1]
        k = commands[n][2]
        answer.append(sorted(array[i-1:j])[k-1])
    
    return answer
```

- `sort()` 를 사용하는 경우 deepcopy 를 사용해서 문제를 풀었다.

```python
import copy 

def solution(array, commands):
    answer = []
    
    for n in range(len(commands)):
        i = commands[n][0]
        j = commands[n][1]
        k = commands[n][2]
        temp_array = copy.deepcopy(array[i-1:j])
        temp_array.sort()
        answer.append(temp_array[k-1])
    
    return answer
```
