## h - index
https://programmers.co.kr/learn/courses/30/lessons/42747

### 문제 
H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과1에 따르면, H-Index는 다음과 같이 구합니다.
어떤 과학자가 발표한 논문 n편 중, **h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값** 이 이 과학자의 H-Index입니다.
어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.

### 문제 예제
1. case1

```
citations
[3, 0, 6, 1, 5]
return 
3

[0, 1, 3, 5, 6]
총 5개의 논문이 있음 (n=5)

1. h_index = 5, num = 0
인용횟수가 5이상인 논문의 수 2
인용횟수가 5이하인 논문의 수 4
2. h_index = 4, num = 1
인용횟수가 4이상인 논문의 수 2
인용횟수가 4이하인 논문의 수 3
3. h_index = 3, num = 3 -> h-index = 3
인용횟수가 3이상인 논문의 수 3
인용횟수가 3이하인 논문의 수 3
4. h_index = 2, num = 0 
인용횟수가 2이상인 논문의 수 3
인용횟수가 2이하인 논문의 수 2
5. h_index = 1, num = 0
인용횟수가 1이상인 논문의 수 4
인용횟수가 1이하인 논문의 수 2
```

2. case2

```
[0, 1, 1, 4, 6, 7]
총 6개의 논문이 있음 (n=6)

1. h_index = 6, num = 0
인용횟수가 6이상인 논문의 수 2
인용횟수가 6이하인 논문의 수 5
2. h_index = 5, num = 1
인용횟수가 5이상인 논문의 수 2
인용횟수가 5이하인 논문의 수 4
3. h_index = 4, num = 1
6편중, 4번 이상 인용된 논문이 3편 이상이고 3번 이하 인용
인용횟수가 4이상인 논문의 수 3
인용횟수가 4이하인 논문의 수 3
4. h_index = 3, num = 4 -> h_index = 3
6편 중, 3번 이상 인용된 논문이 3편 이상이고 3번 이하 인용
인용횟수가 3이상인 논문의 수 3
인용횟수가 3이하인 논문의 수 3
5. h_index = 2, num = 6
인용횟수가 2이상인 논문의 수 3
인용횟수가 2이하인 논문의 수 3
6. h_index = 1 num = 7
인용횟수가 1이상인 논문의 수 5
인용횟수가 1이하인 논문의 수 3
```

### 문제풀이
이 문제는 문제 자체를 이해하는데 너무 많은 시간이 걸렸고 결과적으로는 문제를 완벽히 이해하지 못해서 다른분들의 소스코드와 문제풀이 해놓은걸 엄청 읽었다. 

```python

def solution(citations):
    answer = 0
    citations = sorted(citations)

    for i in range(len(citations)):
        h_index = len(citations) - i

        if citations[i] >= h_index:
            answer = h_index
            break

    return answer

```

- 참고: https://caution-dev.tistory.com/11