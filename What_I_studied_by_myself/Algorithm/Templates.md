# Templates 

### BFS

- 한 번에 한 단계씩 발전하여,
- 목적지까지 가는데 걸리는 시간 구하기, 갈 수있느냐의 여부, 어디가 제일 좋은 위치인가에 대한 판단을 한다.
- 초기에 queue나 visited를 생성한다.

``` python
# 미로의 거리
def bfs(si, sj, ei, ej):
    q = []									# queue 생성
    visited = [[0] * N for _ in range(N)]
    
    q.append([si, sj, 0])					# queue에 초기데이터 삽입
    visited[si][sj] = 1
    
    while q:
        ci, cj, d = q.pop(0)				# queue에서 하나를 꺼낸 다음,
        if ci==ei and cj==ej:				# 종료조건을 처리하는 문
            return d-1
        for di, dj in ([-1, 0], [1, 0], [0, -1], [0, 1]):	# 다음좌표로의 이동을 나타내는 반복문
            ni, nj = ci + di, cj + dj
            if 0<=ni<=N and 0<=nj<=N and visited[ni][nj]==0 and MAP[ni][nj]!='1':# 범위 내에 있고 방문하지 않았으며 벽이 아닐경우
                q.append([ni, nj, d+1])
                visited[ni][nj] = 1
     return 0

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    MAP = [list(input()) for _ in range(N)]
    
```

- 관련문제(SWEA) : 100__미로의 거리, 101_contact, 102_정사각형방, 103_탈주범검거



### DFS/백트래킹

- 관련문제(SWEA) :  104_Stack2_연습2_부분집합, 105_장훈이의높은선반,106__요리사
- **가능한 모든 경우**를 처리해서 답을 찾는 문제
  - 시간초과를 고려해야 한다.
  - 종료조건을 잘 체크해야 한다. (기본적으로 n 관련)
- 가능한 모든 경우를 표현하는 효율적인 방법은 Tree(상태 공간 트리 설계)

``` python
# 104_Stack2_연습2_부분집합
def DFS(n, num):
    global sol
    if sum > K:						# 가지치기(풀이 후 가장 마지막에 고려)
        return
    if n >= N:						# 종료조건(n에 관한)
        if sum == K:
            sol += 1
        return
    DFS(n+1, sum+lst[n])			# 숫자를 포함하는 경우
    DFS(n+1, sum)					# 숫자를 포함하지 않는 경우
    
T = int(input())

for test_case in range(1, T+1):
    N, K = map(int, input().split())
    lst = list(map(int, input().split()))
    sol = 0
    DFS(0, 0)						# 제일 상단(원점)
    print(f'#{test_case} {sol}')
```

- 가지치기는 풀이 후 마지막에 고려하도록 한다.
- 먼저 종료조건부터 고려한다.
