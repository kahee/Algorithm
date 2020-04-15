## 탐욕 알고리즘

- 최적의 해에 가까운값을 구하기 위해 사용함 
- 매순간 최적이라고 생각되는 경우를 선택함
- 조합을 생각하지 않음 

### 예시

1. 동전문제
- 지불해야하는 값이 있고 각 동전들의 조합을 이용하되, 가장 적은 동전의 수를 이용해야함

```python
coin_list = [500, 100, 50, 1]
def min_coin_count(value, coin_list):
    total_coin_count = 0
    details = list()
    coin_list.sort(reverse=True)

    for coin in coin_list:
        coin_num = value // coin  # 최대값을 구함
        total_coin_count += coin_num
        value -= coin_num * coin
        detils.append([coin, coin_num])

    return total_coin_count
```

2. 부분 배낭 문제
- 무게 제한이 k 인 배낭에 최대 가치를 가지도록 물건을 넣는 문제 
    - 물건은 쪼개 넣을 수 있음

```python
# (무게, 가치)
data_list = [(10, 10), (15, 12), (25, 8), (30, 5)]

def get_max_value(data_list, capacity):
    # 가치가 높은 것부터
    data_list = sorted(data_list, key=lambdax:x[1]/x[0], reverse=True)
    total_value = 0
    details = list()

    for data in data_list:
        if capacity - data[0] >= 0:
            capacity -= data[0]
            total_value += data[1]
            details.append([data[0], data[1], 1])
        else:
            fraction = capacity / data[0]
            capacity -= data[0] * fraction
            total_value += data[1] * function
            details.append([data[0], data[1], fraction])

    return total_value, details
```

### 한계
- 반드시 최적의 해를 구할 수 있는것은 아님
- 근사치 추정에 활용함
