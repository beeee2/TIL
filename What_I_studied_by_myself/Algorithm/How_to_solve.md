# 시간복잡도

- 우리가 보통 말하는 시간 복잡도는 O(n)보다 세타라는 표현이 맞다.

  - 연산 수가 n에 비례 한다 => O(n)

  - 연산 수가 n**2에 비례 한다  => O(n^2)



- 시간적으로 의미있는 수치만 기재한다.
  - 계수 정렬의 경우 O(N + K)이다.



[문제 관련 Tip]

- 시간제한의 경우 1초는 연산 1억까지 가능하다는 의미다.
- 연산크기에 딱 맞게 설계하는 것은 좋지 않다.
- 순열
  - 시간복잡도가 n!
  - n 제한이 8~10이라면 1번 혹은 2번 템플릿이 사용가능하다.

- 조합
  - 시간복잡도가 2^n 
  - n 제한이 15~20이 나온다.
  - 백트래킹 3, 4번 템플릿을 사용할 수 있다.

- 3중 for

  - 시간복잡도가 n^3
  - n 제한이 100~300이 나온다.

- 2차원 DP

  - 시간복잡도가 n^2 ~ n^3

  - n 제한이 100~1000, 300~500 => 어지간하면 2차원 DP라고 보면된다.

- 2중 for
  - 시간복잡도가 n^2
  - n 제한이 1000~3000으로 주어진다.
- 정렬, 이진탐색
  - 시간복잡도가 nlogn
  - n 제한이 100,000 ~ 200,000
- 스택, 투포인터
  - 시간복잡도가 n
  - n 제한이 100,000 ~ 1,000,000



# 메모리 제한

- int 하나에 파이썬은 8byte라고 생각하면 편하다.
  - int 1000개 사용이 8kb, 100만개 8mb
- DFS로 짰을 때 통과가 안되면 BFS로 작성한다.



# 그래프 탐색

- 자료구조

  - 스택,  큐, 덱, 그래프, 트리

  - 선형 자료구조, 비선형 자료구조

- 선형 자료구조

  - 스택, 큐, 덱
  - 데이터간의 **순서**만 중요하다.

- 비선형 자료구조

  - 데이터간의 **관계**를 저장한다.
  - 그래프, 트리



- 그래프
  - 간선은 필수요소가 아니다.
  - 서로 연결된 것들을 연결 요소, **conntected component**
  - 연결 요소의 갯수는 보통 노드의 개수를 의미한다. 



[문제 관련 Tip]

- DFS, BFS => 연결 요소
- DFS => 경로 정보, 이전으로 돌아간다, 이제까지 왔던 길에 이것들이 몇개 있냐
- BFS => 최단거리



## DFS

- **시작점과 연결된 모든 연결요소들이 방문처리를 할 수 있다.**
-  문제유형
  1) 시작노드 s, 끝노드, s에서 e를 갈 수 있는가? 
     - S에서 DFS를 돌려서 E가 방문처리 되어있는지 확인하여 문제를 풀 수 있다. 
  2) S가 포함된 연결 요소의 크기를 구하시오.
     - S에서 DFS를 돌린 후 방문처리된 노드의 수를 구한다.
  3) 연결 요소의 개수를 구하시오
     - 방문 안한 노드를 볼 때마다 카운트 후 DFS를 사용한다.



```python
n = int(input()) 
m = int(input()) 

v = [[] for i in range(n+1)]

for i in range(m):
    a, b = map(int, input().split())
    
    v[a].append(b)
    v[b].append(a)

visited = [False for i in range(n+1)]

def dfs(cur): #cur번 dfs 도는 것
    visited[cur] = True
    
    for nxt in v[cur]:
        # 연결된 애들을 살펴본다.
        if visited[nxt]:
            continue
        
        dfs(nxt)
    
dfs(1)

cnt = 0
for i in range(n+1):
    if visited[i]:
        cnt += 1
        
print(cnt - 1)
    
```

```python
# 연결된 노드의 개수 (크기 구하기)
n = int(input()) 
m = int(input()) 

v = [[] for i in range(n+1)]

for i in range(m):
    a, b = map(int, input().split())
    
    v[a].append(b)
    v[b].append(a)

visited = [False for i in range(n+1)]

def dfs(cur): #cur번 dfs 도는 것
    cnt = 1
    visited[cur] = True
    
    for nxt in v[cur]:
        # 연결된 애들을 살펴본다.
        if visited[nxt]:
            cnt += 1
            continue
        
        cnt += dfs(nxt)
    return cnt
    

print(dfs(1))
    
```



``` python
#연결요수의 개수 구하기
n, m = map(int, input().split())
v = [[] for i in range(n+1)]

for i in range(m):
    a, b = map(int, input().split())
    
    v[a].append(b)
    v[b].append(a)
    
visited = [False for i in range(n+1)]

def dfs(cur):
    visited[cur] = True
    
    for nxt in v[cur]:
        if visited[nxt]:
            continue
        
        dfs(nxt)
        
cnt = 0
for i in range(1, n+1):
    if not visited[i]:
        cnt += 1
        dfs(i)

print(cnt)
```

``` python
# 연결요소에서 가장작은 값구하기
n, m, k = map(int, input().split())
arr = [0] + list(map(int,input().split()))
v = [[] for i in range(n+1)]

for i in range(m):
    a, b = map(int, input().split())
    
    v[a].append(b)
    v[b].append(a)

visited = [False for i in range(n+1)]

def dfs(cur):
    ret = arr[cur] # 내가 얼만지 
    visited[cur] = True
    for nxt in v[cur]:
        if visited[nxt]:
            continue
        
        ret = min(ret, dfs(nxt))
    return ret
ans = 0
for i in range(1, n+1):
    if visited[i]:
        continue
    ans += dfs(i)
    
print(ans)
```

``` python
# 플러드 필, flood fill
# 0은 노드가 없는 위치, 1은 노드가 있는 위치
# 상하좌우 간선이 존재한다고 보면 그래프 문제
# 많이 풀어보기, 유기농배추, 섬의 개수, 영역구하기,

n = int(input())
arr = [input()] for i in range(n)]
visited = [[False for i in range(n)] for j in range(n)] # n * n개 만큼 방문처리 리스트를 만들어줘야 한다.
dx = [1, 0, -1 , 0]
dy = [0, 1, 0, -1]

def in_range(x, y):
    return 0 <= x < n and 0 <= y < n

def dfs(x, y): # 좌표 x, y 두개가 필요하다.
    ret = 1
    visited[x][y] = True
    
    for i in range(4):
        nx = x + dx[i]
        ny = y + dy[i]
        
        if not in_range(nx, ny) or visited[nx][ny]:
            continue
        ret += dfs(nx, ny)
    return ret

# 노드 하나 -> 정수 두개(좌표)로 표현된다.
cnt = 0
ans = []
for i in range(n):
    for j in range(n):
        if visited[i][j] or arr[i][j] == '0':
            continue
        cnt += 1
        ans.append(dfs(i,j))
        
ans.sort()

print(cnt)
for i in ans:
    print(i)


```



# BFS

``` python
# 덱을 사용한다.
n = int(input())
m = int(input())
v = [[] for i in range(n+1)]

for i in range(m):
    a, b = map(int, input().split())
    v[a].append(b)
    v[b].append(a)
    
que = deque()
visited = [False for i in range(n+1)]

que.append(1)
visited[1] = True
while len(que) > 0:
    cur = que[0]
    que.popleft()
    
    for nxt in v[cur]:
        if visited[nxt]:
            continue
        que.append(nxt)
        visited[nxt] = True
```

- Que에 넣는 것과 방문처리가 딱 붙어 있어야 한다.

- 최단 거리 구할 때만 BFS를 쓴다.

``` python
from collections import deque
n, m = map(int,input().split())
que = deque()
visited = [False for i in range(200010)]

que.append(n)
visited[n] = True

while len(que) > 0:
    cur = que.popleft()
    
    for nxt in [cur-1, cur+1, 2*cur]:
        if not (0 <= nxt < 200010) or visited[nxt]:
            continue
        que.append(nxt)
        visited[nxt] = True
    
# 한 가지 방법

```



# 트리

- 트리란?
  - 모든 노드가 하나의 연결요소다
  - 사이클이 없다.
- 트리를 다르게 표현하면?
  - 노드의 개수가 N일때, 간선의 개수가 N -1이다.
  - 모든 노드가 하나의 연결요소다. 사이클이 없다.

- Rooted Tree 
  - 루트가 있는 트리
  - 상하관계가 존재한다. (부모/자식/자손 등)
  - 서브트리의 개념이 존재한다.
    - 아무 노드나 잡고 해당 노드를 루트로 두었을 때 이게 서브트리에 해당한다.

``` python
par = [0 for i in range(n+1)] #부모를 저장할 배열

def dfs(cur, prv):
    par[cur] = prv
    for nxt in v[cur]:
        if nxt == prv:
            continue
            
        dfs(nxt, cur)
```

- 사이클이 없기때문에 무한 루프가 생성되지 않는다.

```python
#LCA, 가장 낮은 조상(조상 중 깊이가 가장 깊은 조상)
```

