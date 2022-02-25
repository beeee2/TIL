# 큐



## 큐

### ✏ 큐(Queue)의 특성

- 스택과 마찬가지로 삽입과 삭제의 위치가 제한적인 자료 구조
  - 큐의 뒤에서는 삽입만 하고, 큐의 앞에서는 삭제만 이루어지는 궂
- 선입선출구조(FIFO : First in First Out)
  - 큐에 삽입한 순서대로 원소가 저장되어, 가장 먼저 삽입된 워ㅜㄴ소는 가장먼저 삭제된다.



### ✏ 큐의 선입선출 구조

- 앞쪽에서 나간다(삭제), 뒤쪽에서 들어온다(삽입)
- 두 개의 인덱스가 필요하다.
- 저장된 원소 중 첫 번째 원소, 머리(Front)/ 저장된 원소 중 마지막 원소, 꼬리(Rear)



### ✏ 큐의 기본 연산

- 삽입 : enQueue
- 삭제 : deQueue



### ✏ 큐의 사용을 위해 필요한 주요 연산

- enQueue(item) : 큐의 뒤쪽(rear 다음)에 원소를 삽입하는 연산
- deQueue() : 큐의 앞쪽(front)에서 원소를 삭제하고 반환하는 연산

- createQueue(), isEmpty(), isFull(), Qpeek()



### ✏ 선형 큐의 연산 과정

#### 1) 공백 큐 생성 : createQueue();

- 초깃값 : front=rear= -1
  - 한 번도 저장된적도 삭제된 적도 없다는 이야기
- front 는 마지막으로 삭제된 위치, rear는 마지막으로 저장된 위치

#### 2) 원소 A 삽입 : enQueue(A)

- rear가 가리키는 자리에 A를 삽입한다.

#### 3) 원소 반환/삭제 : deQueue()

- front = rear 는 마지막까지 다 비어졌다는 의미 (Queue가 비어있는 상태)

  

## 큐의 구현

### ✏ 선형큐

- 1차원 배열을 이용한 큐
  - 큐의 크기 = 배열의 크기
  - front : 저장된 첫 번째 원소의 인덱스
  - rear : 저장된 마지막 원소의 인덱스

- 상태표현
  - 초기 상태 : front = rear = -1
  - 공백 상태 : front == rear
  - 포화 상태 : rear == n-1 (n : 배열의 크기, n-1: 배열의 마지막 인덱스)

- 검색 : Qpeek()
  - 가장 앞에 있는 원소를 검색하여 반환하는 연산
  - 현재 front의 한 자리 뒤에 있는 원소, 즉 큐의 첫 번째에 있는 원소를 반환



## 선형 큐 이용시의 문제점

### ✏ 잘못된 포화상태 인식

- 선형 큐를 이용하여 원소의 삽입과 삭제를 계속할 경우, 배열의 앞부분에 활용할 수 있는 공간이 있음에도 불구하고, rear = n - 1 인 상태 즉, 포화상태로 인식하여 더 이상의 삽입을 수행하지 않게 됨

#### ✏  해결방법 1

- 큐의 원소들을 이동하는 것은 시간이 너무 오래걸려 효율성이 떨어진다.

#### ✏ 해결방법2

- 1차원 배열을 사용하되, 논리적으로는 배열의 처음과 끝이 연결되어 원형 형태의 큐를 이룬다고 가정하고 사용



## 원형 큐의 구조

#### ✏ 초기 공백 상태

- front = rear= 0
- 크기 n인 1차원 배열을 생성

#### ✏  Index의 순환

- front와 rear의 위치가 배열의 마지막 인덱스인 n-1를 가리킨 후, 그 다음에는 논리적 순환을 이루어 배열의 처음 인덱스인 0으로 이동해야함
- 이를 위해 나머지 연산자 mod를 사용함

#### ✏ front 변수

- 공백 상태와 포화상태 구분을 쉽게 하기 위해 front가 있는 자리는 사용하지 않고 항상 빈자리로 둔다
- 원형큐에서 rear, front가 n으로 돌아가면 mod n 시 1이 된다..

#### 공백상태 및 포화상태 검사 : isEmpty(), isFull()

- 공백상태  : front == rear

- 포화상태 : 삽입할 rear의 다음 위치 == 현재 front

  - (rear + 1) mod n == front

    ``` python
    def isEmpty(): #공백상태
        return front == rear
    
    def isFull(): 
        return (rear+1) % len(cQ) == front
    ```

- 삽입(enQueue(item))

  ``` python
  def enQueue(item):
      global rear
      if isFull():
          print('Queue_Full')
      else:
          rear = (reat + 1) % len(cQ)
          cQ[rear] = item
  ```

- 삭제(deQueue(), delete())

  - 가장 앞에있는 원소를 삭제하기 위해

    1) front 값을 조정하여 삭제할 자리를 준비함

    2) 새로운 front 원소를 리넡함으로써 삭제와 동일한 기능함

       ``` python
       def deQueue():
           global front
           if isEmpty():
               print("Queue_Empty")
           else:
               front = (front + 1) % len(cQ)
               return cQ[front]
       
       def delete():
           global front
           if isEmpty():
               print("Queue_Empty")
           else:
               front = (front + 1) % len(cQ)
               
       def isEmpty():
           return front == rear
       def isFull():
           return (rear + 1) % len(cQ) == front
       ```

       

## 우선순위 큐(Priority Queue)

#### 우선순위 큐의 특성

- 우선순위를 가진 항목들을 저장하는 큐
- FIFO 순서가 아니라 우선순위가 높은 순서대로 먼저 나가게 된다.

#### 우선순위 큐의 적용 분야

- 시뮬레이션 시스템
- 네트워크 트래픽 제어
- 운영체제의 테스크 스케줄링



## 큐의 활용 : 버퍼(Buffer)

#### ✏ 버퍼

- 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리의 영역
- 버퍼링 : 버퍼를 활용하는 방식 또는 버퍼를 채우는 동작을 의미한다.



#### ✏ 버퍼의 자료구조

- 버퍼는 일반적으로 입출력 및 네트워크와 관련된 기능에서 이용된다
- 순서대로 입력/출력/전달되어야 하므로 FIFO 방식의 자료구조인 큐가 활용된다.



## BFS(Breadth First Search)

- 그래프를 탐색하는 방법에는 크게 두 가지가 있다.
  - 깊이우선탐색(DFS), 너비우선탐색(BFS)

- 너비 우선 탐색은 탐색 시작점의 인접한 정점들을 먼저 모두 차례로 방문한 후, 방문했던 정점을 시작점으로 하여 다시 인접한 점정들을 차례로 방문하는 방식
- DFS와 BFS의 차이에 대해 생각해보자
- 큐가 비면 탐색이 끝난다.
- 중복이 많이 존재할 경우 큐의 크기를 지정하기 애매하다. 

(강의안 오타 / 입력파라미터: 60page)

- 마지막에 visited[n]을 visited[t]로 수정할 것 