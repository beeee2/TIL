# List2



### 2차원 배열의 선언

- 1차원 List를 묶어놓은 List
- 2차원 이상의 다차원 List는 차원에 따라 Index를 선언
- 2차원 List의 선언 : 세로 길이(행의 개수), 가로 길이(열의 개수)를 필요로 한다.
- Python에서는 데이터 초기화를 통해 변수 선언과 초기화가 가능하다.



### 배열 생성

``` python
N = int(input())

arr = [list(map(int, input().split())) for _ in range(N)]
```



### 배열 순회

- N * M 배열의 n * m 개의 모든 원소를 빠짐없이 조사하는 방법

#### 행 우선 순회

- i 행의 좌표

- j 열의 좌표

  ``` python
  for i in range(n):
      for j in range(m):
          Array[i][j] #필요한 연산 수행
  ```

- 주의사항, 아래와 같이 사용하지 말아야 한다.

  ``` python
  arr = [[0] * 3] * 4
  # 2차원 배열은 위와 같이 생성하지 않는다. 
  # 얕은 복사가 된다.
  '''
  arr[0][1] = 1 출력시
  [[0, 1, 0], [0, 1, 0], [0, 1, 0], [0, 1, 0]]으로 출력된다.
  '''
  ```

#### 열 우선 순회

- i 행의 좌표

- j 열의 좌표

  ``` python
  for j in range(m):
      for i in range(n):
          Array[i][j] # 필요한 연산 수행
  ```

#### 지그재그 순회

- i 행의 좌표

- j  열의 좌표

  ``` python
  for i in range(n):
      for j in range(m):
          Array[i][j + (m-1-2*j) * (i % 2)]
  ```

#### 델타를 이용한 2차 배열 탐색

- 2차 배열의 한 좌표에서 4방향의 인접 배열 요소를 탐색하는 방법

- 2차원 배열 더하기 (**질문**)

  ``` python
  N = int(input())
  arr2 = [[0]*(N+1)] + [0][list(map(int, input().split())) for _ in range(N)]
  arr3 = [[0]*(N+2)] + [0]+[list(map(int, input().split()))+[0] for _ in range(N)] + [[0]*(N+2)]

- 델타를 이용한 2차원 배열

  ``` python
  di = [0, 1, 0, -1]
  dj = [1, 0, -1, 0]
  
  for di, dj in[(0,1), (1,0), (0, -1), (-1, 0)]:
      ni = i + di
      nj = j + dj
      if 0 <= ni < N and 0 <= nj < M: #유효인덱스
          arr[ni][nj]
  ```

  ``` python
  arr=[0...N-1][0...M-1]
  di[] = [-1, 1, 0, 0]
  dj[] = [0, 0, -1, 1]
  for i in range(N):
      for j in range(M):
          for k in range(4):
              ni = i + di[k]
              nj = j + dj[k]
              if 0 <= ni < N and 0 <= nj < M: #유효한 인덱스면
                  test(arr[ni][nj])
  ```

  

#### 전치 행렬

- 모든 원소가 아닌 일정 부분의 원소를 사용하여 전치 시켜야 한다. (어느 한 쪽만 기준으로 삼는다.)

- 모든 원소가 적용되면 처음으로 돌아가기 때문이다.

  ``` python
  # i : 행의 좌표, len(arr)
  # j : 열의 좌표, len(arr[0])
  arr =[[1,2,3] , [4,5,6], [7,8,9]] # 3*3행렬
  
  for i in range(3):
      for j in range(3):
          if i < j:
              arr[i][j], arr[j][i] = arr[j][i], arr[i][j]
  ```

  

  