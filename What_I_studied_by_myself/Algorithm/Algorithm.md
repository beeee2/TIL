# DFS와 BFS

## 들어가기에 앞서

### 자료구조

- 스택, 큐, 덱 
  - 선형자료구조
  - 데이터를 들어간 순서에 맞게 저장한다
  - 데이터 간의 관계는 고려하지 않는다.
  - 데이터의 순서를 고려한다.
- 그래프, 트리
  - 비선형자료구조
  - 데이터 간의 관계를 고려한다.
  - 구성요소로 노드(혹은 정점)와 엣지(혹은 간선)가 있다.
  - 노드만 존재하더라도 그래프에 해당한다.
  - 직, 간접적으로 연결되어있는 요소들을 **연결요소**(Connected component)라고 한다.





## DFS

### DFS를 이용한 문제 유형

- 특정 지점을 시작으로 DFS를 돌렸다면 시작한 노드와 연결관계에 있는 요소들을 방문처리할 수 있다.
- '**s에서 e를 갈 수 있는가**'
  - s에서 DFS 돌린 후 e가 방문처리 되어 있는지 확인한다.
- **'s가 포함된 연결요소의 크기'**
  - s에서 DFS 돌린 후 방문처리된 노드의 개수를 구하면 된다.
  - 관련 문제
    - 바이러스(백준)
- **'연결요소의 개수 세기'**
  - 방문처리가 안 된 노드를 구할 때마다 COUNT 후 DFS 돌리기



### 기본형 코드

- 그래프의 연결 정보를 저장할 2차원 리스트를 생성한다.
- 방문 여부를 확인할 리스트를 생성한다.


#### 바이러스(백준)

``` python
n = int(input())
m = int(input())

v = [[] for i in range(n+1)]

for i in range(m):
    a, b = map(int, input().split())
    
    v[a].append(b)			# a에서 갈 수 있는 노드로 b가 생겼다.
    v[b].append(a)			# b에서 갈 수 있는 노드로 a가 생겼다.
    
visited = [False for i in range(n+1)]

def dfs(cur):
    cnt = 1
    visited[cur] = True		# 현재 노드 방문처리
    cnt += 1
    
    for nxt in v[cur]: 
        if visited[nxt]:
            continue
        cnt += dfs(nxt)
        	
    return cnt
        
        
print(dfs(1))
```



#### 연결요소의 개수

``` python
def dfs(cur):
    visited[cur] = True

    for nxt in graph[cur]:
        if visited[nxt]:
            continue

        dfs(nxt)

N, M = map(int, input().split())
graph = [[] for _ in range(N+1)]
visited = [False for _ in range(N+1)]
cnt = 0
for _ in range(M):
    a, b = map(int, input().split())
    graph[a].append(b)
    graph[b].append(a)

for i in range(1, N+1):
    if not visited[i]:
        cnt += 1
        dfs(i)

print(cnt)
```





## BFS



## DFS, BFS 그리고 문제풀이

### 문제 풀이

- DFS, BFS가 모두 가능할 때는 '연결요소'에 관한 문제들 
- DFS만 가능할 때는 경로 정보, 이전으로 돌아간다거나, 이제까지 왔떤 길에 특정 요소가 몇개있나 등을 파악할 때
- BFS만 가능할 때는, 최단거리를 구할 때



---

# 🌱  DP

















