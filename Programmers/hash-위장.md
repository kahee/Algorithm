## 위장
https://programmers.co.kr/learn/courses/30/lessons/42578

### 문제풀이 
- (옷 category갯수 * category 갯수) 이런식으로 경우의 수를 구하면 된다고 생각하여 문제를 풀었으나 오답
- 이렇게 하는 경우 반드시 하나씩만 걸치는 경우만 포함된다. 따라서 해당 카테고리 아이템을 장착하지 않은 경우를 1씩 더해줘야 한다. 
예를 들어 (안경: 파란안경, 빨간안경), (옷: 반팔) 옷만 입고 안경을 안쓰는 경우는 해당이 되지 않는다. 마지막으로 -1 을 빼는 경우는 
해당 문제에서 스파이는 무조건 한개이상의 아이템을 장착해야한다고 했기 때문에 어떠한 아이템을 사용하지 않는 경우의 수를 빼줘야 한다. 

```python 
import collections
from collections import defaultdict
def solution(clothes):
    cloathes_dict = defaultdict(int)
    answer = 1
    for i in clothes:
        category = i[1]
        item = i[0]
        cloathes_dict[category] += 1
    
    for key in cloathes_dict.keys():
        answer *= (cloathes_dict[key] + 1)
        
    return answer - 1
```

### 오답
```python 
import collections
from collections import defaultdict
def solution(clothes):
    cloathes_dict = defaultdict(int)
    answer = 0
    for i in clothes:
        category = i[1]
        item = i[0]
        cloathes_dict[category] += 1
        answer += 1
    
    temp = 1
    for item in cloathes_dict.items():
        temp *= item[1]
        
    answer += temp
    return answer
```