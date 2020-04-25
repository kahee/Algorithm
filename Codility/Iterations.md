## Iterations
https://app.codility.com/programmers/lessons/1-iterations/

### 문제 풀이

```python
import re

def convert_to_binary(number:int) -> str:
    return bin(number).replace("0b","")

def solution(N):
    # write your code in Python 3.6
    binary_number = convert_to_binary(N)
    binary_gap_list = re.findall(r'(0+)1', binary_number)
    if binary_gap_list:
        max_binary_gap = max(binary_gap_list)
        return len(max_binary_gap)
    else:
        return 0
```

### 오답
- 이렇게 하는 경우 1000010001 이진수인 경우 앞에 0000 은 찾으나 뒤에 binary_gap 을 찾지 못하는 문제가 있었다. 
- 정규표현식을 (0+)1 로 끝나는 표현으로 변경 

```python 
import re

def convert_to_binary(number:int) -> str:
    return bin(number).replace("0b","")

def solution(N):
    # write your code in Python 3.6
    binary_number = convert_to_binary(N)
    binary_gap_list = re.findall(r'1(0+)1', binary_number)
    if binary_gap_list:
        max_binary_gap = max(binary_gap_list)
        return len(max_binary_gap)
    else:
        return 0
```