# 📚백트래킹



### 정의

- 완전 탐색을 하는 도중, 현재 탐색이 무의미한 경우 되돌아가는 알고리즘
- 전수 검사를 하지 않고 무의미한 작업들을 **가지치기**하는 방법을 백트래킹이라고 한다.
  - 가지치기(pruning) : 유망하지 않는 노드가 포함되는 경로는 더이상 고려하지 않는 것.

-  백트래킹 기법은 **최적화(optimization) 문제**와 **결정(decision) 문제**를 해결할 수 있다.
  - 최적화 - A에서 출발해 B로 도착하기 위해 이용할 가장 좋은 경로 찾기
  - 결정문제 
    - 문제의 조건을 만족하는 해가 존재하는 지의 여부를 yes 또는 no가 답하는 문제
    - A에서 B로 갈 수 있는지, 경로 중에서 하나 찾기
      - ex) 미로찾기, n-Queen문제, 부분집합의 합(Subset Sum)문제 등

- 백트래킹 알고리즘을 적용하면 일반적으로 경우의 수가 줄어들지만 이 역시 최악의 경우에는 여전히 지수함수 시간(Exponential Time)을 요하므로 처리가 불가능하다. (2 ** N ...)
- **재귀로 구현**한다.



### 과정

- 여러가지 선택(옵션)들이 존재하는 상황에서 한가지를 선택한다.
- 선택이 이루어지면 새로운 선택지들의 집합이 생성된다.
- 이런 선택을 반복하면서 최종상태에 도달한다.
  - 올바른 선택을 계속하면 목표 상태(goal state)에 도달한다.



### 코드

- N-Queen 문제 : n*n 의 공간에  n개의 퀸을 놓는 문제. 대각선과 가로 세로 방향에 이제 퀸을 더이상 놓을 수 없는 문제.

``` python
def checknode(V):						# node
    if promisiong(V):
        if there is a solution at V:
            write the solution
        else:
            for u in each child of v:
                checknode(u)
```



``` python
# 수도코드
backtrack(a[], k, input):	
    c[MAXCANDIDATES]					# 후보군을 저장할 배열
    ncands								# 후보의 수(len으로 구한 값)
    
    IF k == input: process_solution(a[], k)	# 내가 원하는 갯수만큼 후보군이 채워졌으면,
        # process_solution 함수에서 원하는 값을 찾으라는 의미
    ELSE:
        k ++
        make_candidates(a[], k, input, c[], ncands)	# 후보를 추천해주는 함수
        # a는 추천한 후보에 대해 결정한 결과
        # 현재선택한 개수 k
        # 추천한 후보군을 c에 넣는다.
        # 후보군의 개수 ncands
        FOR i in 0 -> ncands - 1
        	a[k] <- c[i]
            backtrack(a, k, input)	# 다음 번 후보를 고르러 이동한다.
main()
	a[MAX]			# powerset을 저장할 배열
    backtrack(a[], 0, 3) # 3개의 원소를 가지는 powerset


make_candidates(a[], k, n, c[], ncands):
    c[0] <- TRUE
    c[1] <- FALSE
    ncands <- 2
    
process_solution(a[], k)
	FOR i in 1 -> k:
       IF a[i] == TRUE : print(i)
```



#### 백트래킹을 이용하여 순열 구하기

