## 가장큰수 
https://programmers.co.kr/learn/courses/30/lessons/42746

### 문제풀이
- 우선 자리수가 1개인 수중에 가장 큰 수를 앞으로 
- 길이가 같은 수의 경우엔 뒷자리 수가 큰수로 -> 이런경우 모든 수를 다 비교해봐야한다. (그러기 때문에 이것도 시간이 오래 걸림)
- 다른분 풀이를 참고해보니 a+b > b+a 비교를 통해 숫자를 정렬하는 방식으로 해결 `

```python

def solution(numbers):
    str_numbers = list(str(i) for i in numbers)
    from _functools import cmp_to_key
    answer_list = sorted(str_numbers, key=cmp_to_key(lambda x, y: int(x+y) - int(y+x)), reverse=True)
    answer = "".join(answer_list)
    return answer if answer[0] != "0" else "0"

```
- `cmp_to_key`: 두개의 인자를 받아서 그 인자를 비교하는 함수로서 작으면 음수, 같으면 0 크면 양수 반환
- python 내장함수인 sorted, sort 함수는 어떤 알고리즘을 사용하는가? https://shifu-oh.tistory.com/5 
- https://medium.com/@rylanbauermeister/understanding-timsort-191c758a42f3

### 오답
- 시간초과 
- python 내장함수를 이용하면 간단하게 될것 같았는데 시간초과 

```python 
from itertools import permutations

def solution(numbers):
    str_num = ''
    for i in numbers:
        str_num += str(i)
        
    combinations_list = list(permutations(numbers))
    max_num = None
    for i in combinations_list:
        number = "".join(map(str, i))
        if not max_num or int(max_num) < int(number):
            max_num = number
    return max_num
```

### 수학 개념
- 순열(Permutation): 서로 다른 N개에서 R개를 택하여 일렬로 나열하는 것 -> **순서를 정해서 나열**
    - ex) 5명의 후보중에서 한명은 회장, 한명은 부회장
- 조합(Combination): 순서를 생각하지 않음 
    - ex) 5명의 후보중에서 2명의 부회장을 뽑는방법

### 구현 로직
https://shoark7.github.io/programming/algorithm/Permutations-and-Combinations