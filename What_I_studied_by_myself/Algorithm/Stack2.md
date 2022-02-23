# 📚 Stack2



## 📕 DFS(깊이우선탐색)

- 비선형구조인 그래프 구조는 그래프로 표현된 모든 자료를 빠짐없이 검색하는 것이 중요함
- 두 가지 방법
  - 깊이 우선 탐색(Depth First Search, DFS)
  - 너비 우선 탐색(Breadth First Search, BFS)



### ✏ DFS(깊이우선탐색)

- 시작 정점의 한 방향으로 갈 수 있는 경로가 있는 곳까지 깊이 탐색해 가다가 더 이상 갈 곳이 없게 되면, 가장 마지막에 만났던 갈림길 간선이 있는 정점으로 되돌아오서 다른 방향의 정점으로 탐색을 계속 반복하여 결국 모든 정점을 방문하는 순회방법

- 가장 마지막에 만났던 갈림길의 정점으로 되돌아가서 다시 깊이 우선 탐색을 반복해야하므로 후입선출 구조의 스택을 사용

- 재귀와 반복구조를 사용하여 구현할 수 있다.

  - 지나온 길을 저장하고 다시 되돌아가기 위해서 **재귀**와 **스택**을 사용할 수 있다.

  1) 시작 정점 v를 결정하여 방문한다.
  2) 정점 v에 인접한 정점 중에서
     1) 방문하지 않은 정점 w가 있으면, 정점 v를 스택에 push하고 정점 w를 방문한다. 그리고 w를 v로 하여 다시 2)를 반복한다.
     2) 방문하지 않은 정점이 없으면, 탐색의 방향을 바꾸기 위해서 스택을 pop하여 받은 가장 마지막 방문 정점을 v로 하여 다시 2)를 반복한다.
  3) 스택이 공백이 될 때까지 2)를 반복한다.

``` python
visited[], stack[] 초기화
# 리스트는 최소 2개가 필요하다
DFS(v) # v는 시작점
	v 방문;
    visited[v] <- True, #visited는 방문할 수 있는 점의 개수만큼 만들어져 있다
    # ex) visited= [1,0,0,0,0] #0 번점은 방문을 했다는 의미
    do {
        if (v의 인접 정점 중 방문 안한 w 찾기)
        	push(v);
        	while(w) {
                w 방문;
                visited[w] <- True
                push(w);
                v <- w;
                v의 인접 정점 중 방문 안한 w 찾기
            }
        v <- pop(stack);     
    } while(v)
end DFS()
```







## 📒 계산기

- 문자열로 된 계산식이 주어질 때, **스택**을 이용하여 이 계산식의 값을 계산할 수 있다.
- 문자열 수식 계산의 일반적인 방법
  1) 중위표기법의 수식을 후위 표기법으로 변경한다.(**스택이용**)
  2) 후위표기법의 수식을 스택에 이용하여 계산한다.

- 중위 표기법에서 후위 표기법으로의 변환 알고리즘(스택이용)
  1. 입력받은 중위 표기식에서 **토큰**을 읽는다. (문자열에서 최소 단위)
  2. 토큰이 피연산자이면 토큰을 출력한다.
  3. 토큰이 연산자(괄호포함)일 때, 이 토큰이 스택의 top에 저장되어 있는 연산자보다 우선순위가 높으면 스택에 push하고 그렇지 않다면 스택 top의 연산자의 우선순위가 토큰의 우선순위보다 작을 때까지 스택에서 pop한 후 토큰의 연산자를 push한다. 만약 top에 연산자가 없으면 push한다.





## 📗 백트래킹

- 백트래킹(Backtracking) 기법은 해를 찾는 도중에 '막히면'(즉, 해가 아니면) 되돌아가서 다시 해를 찾아 가는 기법이다.
- 백트래킹 기법은 최적화 (optimization) 문제와 결정(decision)문제를 해결할 수 있다.
- 결정 문제 : 문제의 조건을 만족하는 해가 존재하는지의 여부를 'yes' 또는 'no'로 답하는 문제
  - 미로찾기
  - n-Queen 문제
  - Map coloring
  - 부분 집합의 합(Subset Sum) 문제 등

``` python
def backtrack(a, k, input):
    global MAXCANDIDATES
    c = [0] * MAXCANDIDATES
    
    if k == input:
        process_solution(a, k)
    else:
        k += 1
        ncandidates = construct_candidates(a, k, input, c)
        for i in range(ncandidates):
            a[k] = c[i]
            # k 몇개까지 만들었나 #3은 총주어진 갯수
            backtrack(a, k, input)
            
def construct_candidates(a, k, input, c):
    c[0] = True
    c[1] = False
    return 2

MAXCANDIDATES = 2
NMAX = 4
a = [0] * NMAX
backtrack(a, 0, 3)
    
```









## 📙 부분집합, 순열

## 📘 분할정복