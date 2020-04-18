## 전화번호목록 
https://programmers.co.kr/learn/courses/30/lessons/42577

### 문제풀이 
- 문제 이해를 잘 못했었던 것 같다. 결과적으로 사전처럼 sorting 을 하면 앞에 있는 접두어만 보면 되기 때문에 다른 분의 코드를 보고 왔음

```python 
def solution(phone_book):
    # 사전처럼 앞만 보고 비교해도 가능하기 때문에 sort 
    phone_book.sort()

    for i in range(1, len(phone_book)):
        if phone_book[i-1] in phone_book[i]:
            return False
    return True
```

