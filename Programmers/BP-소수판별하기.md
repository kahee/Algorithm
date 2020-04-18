## 소수 판별하기

### 문제 풀이 
- 소수 조건
    N 이 1 이면 소수가 아니다.
    2 부터 N-1 까지의 자연수들로 순서대로 N을 나눠서 나누어 떨어지는 수가 하나도 없으면 N은 소수이다.

```python

from itertools import permutations
def is_prime_number(n: int) -> bool:
    if n < 2:
        return False
    elif n == 2:
        return True
    else:
        for i in range(2, n):
            if n % i == 0:
                return False
    return True

def solution(numbers: List[str]) -> int:
    number_list = list(numbers)
    permutations_number = set()

    for i in range(1, len(number_list) + 1):
        number = list(permutations(number_list, i))
        for j in number:
            permutations_number.add(int(''.join(j)))

    answer = 0
    for num in permutations_number:
        if is_prime_number(num):
            answer += 1
    return answer
```