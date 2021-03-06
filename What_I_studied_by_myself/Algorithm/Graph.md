# 그래프

### 개념

- 그래프는 아이템(사물 또는 추상적 개념)들과 이들 사이의 연결 관계를 표현한다.
- 그래프는 정점(Vertex)들의 집합과 이들을 연결하는 간선(Edge)들의 집합으로 구성된 자료구조다
- V 정점의 개수, E 그래프에 포함된 간선의 개수
  - V개의 정점을 가지는 그래프는 최대 V*(V-1)/2개의 간선이 가능하다.
- 선형 자료구조나 트리 자료구조로 표현하기 어려운 N:N 관계를 가지는 원소들을 표현하기에 용이하다.



### 그래프 유형

- 무향 그래프(Undirected Graph)
- 유향 그래프(Directed Graph)
- 가중치 그래프(Weighted Graph)
- 사이클이 없는 방향 그래프(DAG, Directed Acyclic Graph)
- 완전 그래프
  - 정점들에 대해 가능한 모든 간선들을 가진 그래프
- 부분 그래프
  - 원래 그래프에서 일부의 정점이나 간선을 제외한 그래프



### 인접 정점

- 인접(Adjacency)
  - 두 개의 정점에 간선이 존재(연결됨)하면 서로 인접해 있다고 한다.
  - 완전 그래프에 속한 임의의 두 정점들은 모두 인접해 있다.

### 그래프 경로

- 경로
  - 경로란 간선들을 순서대로 나열한 것이다.
- 경로 중 한 정점을 최대한 한번만 지나는 경로를 단순 경로라고 한다.
- 시작한 정점에서 끝나는 경로를 사이클(Cycle)이라고 한다.

### 그래프 표현

- 간선의 정보를 저장하는 방식, 메모리나 성능을 고려해서 결정한다.
- 인접 행렬(Adjacent matrix)
  - V * V 크기의 2차원 배열을 이용해서 간선 정보를 저장한다.
  - 배열의 배열(포인터 배열)
- 인접 리스트(Adjacent List)
  - 각 정점마다 해당 정점으로 나가는 간선의 정보를 저장
- 간선의 배열
  - 간선(시작 정점, 끝 정점)을 배열에 연속적으로 저장한다.

### 인접 행렬

- 두 정점을 연결하는 간선의 유무를 행렬로 표현한다.
- V * V 정방 행렬
  - 행 번호와 열 번호는 그래프의 정점에 대응
  - 두 정점이 인접되어 있으면 1, 그렇지 않으면 0으로 표현
  - 무향 그래프
    - i 번째 행의 합 = i 번째 열의 합 = Vi의 차수
  - 유향 그래프
    - 행 i의 합 = Vi의 진출차수
    - 열 i의 합 = Vi의 진입 차수

### 인접 리스트

- 각 정점에 대한 인접 정점들을 순차적으로 표현
- 하나의 정점에 대한 인접 정점들을 각각 노드로 하는 연결 리스트로 저장



## 그래프 탐색

### 그래프 순회(탐색)

- 그래프 순회는 비선형구조인 그래프로 표현된 모든 자료(정점)를 빠짐없이 탐색하는 것을 의미한다.

- 그래프 순회 두 가지 방법(***추후 내용 추가)*
  - 깊이 우선 탐색(Depth First Search, DFS)
  - 너비 우선 탐색(Breadth First Search, BFS)





# 최소 비용 신장 트리(MST)

### 개념

- 그래프에서 최소 비용 문제

  1) 모든 정점을 연결하는 간선들의 가중치의 합이 최소가 되는 트리
  2) 두 정점 사이의 최소 비용의 경로 찾기

- 신장 트리

  - N개의 정점으로 이루어진 무방향 그래프에서 N개의 정점과 N-1개의 간선으로 이루어진 트리

- 최소 신장 트리

  - 무방향 가중치 그래프에서 신장 트리를 구성하는 간선들의 가중치의 합이 최소인 신장 트리

    