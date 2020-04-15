## 최단 경로 알고리즘
- 가중치 그래프에서 간선의 가중치 합이 최소가 되는 경로를 찾는 것이 목적

### 문제 종류
- 단일 출발 및 단일 도착 최단 경로 문제
    - 특정 노드를 선택하고 가장 짧은 경로를 찾는것
- 단일 출발 최단 경로 문제 
    - 특정 노드 하나만 고르고 모든 노드간에 최단 거리를 구하는 것
- 전체 쌍 최단 경로

## 다익스트라 알고리즘
- 단일 출발 최단 경로 문제에 해당함

### 코드 

```python 
import heapq 

def dijkstra(graph, start):
    distnaces = {node: float('inf')  for node in graph}
    distnaces[start] = 0 
    queue = []
    heapq.heappush(queue, [distnaces[start], start])
    
    while queue:
        current_distance, current_node = heapq.heappop(queue)
        
        if distnaces[current_node] < current_distance:
            continue
        
        for a, w in graph[current_node].items():
            distnace = current_distance + w

            if distnace < distnaces[a]:
                distnaces[a] = distnace
                heapq.heappush(queue, [distnace, a])
    return distnaces

mygraph = {
    'A':{'B': 8, 'C':1, 'D':2},
    'B':{},
    'C':{'B':5, 'D':2},
    'D':{'E':3, 'F':5},
    'E':{'F':1},
    'F':{'A':5}
}

dijkstra(mygraph, 'A')
{'A': 0, 'B': 6, 'C': 1, 'D': 2, 'E': 5, 'F': 6}
````

