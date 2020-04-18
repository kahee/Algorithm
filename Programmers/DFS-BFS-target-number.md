## Target Number
https://programmers.co.kr/learn/courses/30/lessons/43165
ㄴ
### 문제 풀이 
- 0부터 시작해서 그래프를 시작함

```python 
def solution(numbers, target):
    sup = [0]
    
    for i in numbers:
        sub = []
        for j in sup:
            sub.append(j+i)
            sub.append(j-i)
        sup = sub
        
    return sup.count(target)

# 이런식의 그래프가 생성됨
[1, -1]
[2, 0, 0, -2]
[3, 1, 1, -1, 1, -1, -1, -3]
[4, 2, 2, 0, 2, 0, 0, -2, 2, 0, 0, -2, 0, -2, -2, -4]
[5, 3, 3, 1, 3, 1, 1, -1, 3, 1, 1, -1, 1, -1, -1, -3, 3, 1, 1, -1, 1, -1, -1, -3, 1, -1, -1, -3, -1, -3, -3, -5]
```

### 다른 사람 풀이 
- index 만큼 실행
```python 
answer = 0
def DFS(idx, numbers, target, value):
    global answer
    N = len(numbers)
    if(idx == N and target == value):
        answer += 1
        return
    if(idx == N):
        return

    DFS(idx+1,numbers,target,value+numbers[idx])
    DFS(idx+1,numbers,target,value-numbers[idx])

def solution(numbers, target):
    global answer
    DFS(0,numbers,target,0)
    return answer

```
