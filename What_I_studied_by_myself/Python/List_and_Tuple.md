# 리스트와 튜플

아파트 호수를 보면 알 수 있듯 우리의 일상생활에서도 행과 열의 의미를 가진 **자료의 구조 개념이 녹아있다.**

- 시퀀스형
  - 데이터에 대해 **순서를 가진 자료구조를 총칭** 
  - 시퀀스의 대표적인 자료형이 **리스트와 튜플**이다.



## 리스트의 생성 및 조작법

### 리스트

- 리스트란 **대괄호[]**안에 **서로 다른 자료형의 값을** 콤마(,)로 구분해 **하나 이상 저장**할 수 있는 컬렉션 자료형이다.
- 리스트의 개별항목은 0부터 시작하는 인덱스를 이용해 접근할 수 있다. 
- 저장된 항목은 추후에 변경할 수 있다.

``` python
data_str = "안녕하세요"
data_list = list(data_str) # 개별 문자를 원소로 하는 리스트 객체 생성
print("{0} {1}".format(type(data_list), data_list))
# 출력결과
# <class 'list'>['안', '녕', '하', '세', '요']
```

### 리스트 조작법

#### 리스트 항목 접근

- 인덱스를 이용하여 접근할 수 있다.
- 항목의 개수가 N이라면 마지막 항목은 N-1 인덱스로 접근할 수 있다.
- 유효한 인덱스가 아닌 값을 사용하면 IndexError 예외가 발생한다.
- 인덱스 범위를 지정할 경우 콜론(:)을 사용한다.
- 리스트 객체가 가지고 있는 index(), 인덱스 함수에 항목의 값을 전달하면 해당 항목의 값이 들어 있는 위치의 인덱스를 반환한다.

#### 리스트 기본 연산

cf. 객체의 주소를 알려면 id() 함수를 이용하면 된다.

- 덧셈 연산( + 연산자 )을 통해 두 항목을 연결한 새로운 리스트를 생성할 수 있다.
- '*' 연산자를 이용해 리스트를 여러 번 연결하는 새로운 리스트를 생성할 수 있다.

#### 리스트 항목 추가

- append()를 통해 리스트 항목을 추가할 수 있다.

- insert(인덱스, 항목 값) : 해당 인덱스에 항목 값을 추가할 수 있다.

- extend([항목 값1, 항목 값2]) : 해당 리스트에 해당 값을 지닌 항목들을 각각 추가 할 수 있다.

- append([90, 100])와 같이 append() 함수는 리스트를 전달할 시 리스트를 항목으로 추가한다.

  ``` python
  data_list = [10, 20, 30, 40]
  
  data_list.extend([70, 80]) # 출력결과 data_list: [10,20,30,40,70,80]
  data_list.append([90, 100]) # 출력결과 data_list: [10,20,30,40,70,80,[90, 100]]
  ```

cf. appen() 함수는 반환 값이 없다.



#### 리스트 항목 변경

- 인덱스를 통해 항목을 변경할 수 있다. 
- 인덱스 범위를 지정하여 항목 값들을 변경할 수 있다.
  - ex) data_list[1:3]
  - 이 때 범위 연산자의 마지막 값은 실제 범위에 포함되지 않는다.

``` python
data_list = [10, 20, 30, 40]

data_list[2] = 29
print("data_list : {0}".format(data_list)) # [10, 20, 29, 40]

data_list[1:3] = [12, 15]
print("data_list : {0}".format(data_list)) # [10, 12, 15, 40]

data_list[1:3] = [12, 15, 20]
print("data_list : {0}".format(data_list)) # [10, 12, 15, 20, 40]

data_list[2:3] = [31, 25]
print("data_list : {0}".format(data_list)) # [10, 12, 31, 25, 20, 40], 전체 리스트의 크기가 변경된다.


```



#### 리스트 항목 제거

- del 명령어를 이용해 항목을 제거할 수 있다.

  ``` python
  data_list = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
  
  del data_list[2]
  print("data_list : {0}".format(data_list)) #[10, 20, 40, 50, 60, 70, 80, 90, 100]
  
  del data_list[3:5]
  print("data_list : {0}".format(data_list)) #[10, 20, 40, 70, 80, 90, 100]
  ```

- pop(인덱스) 함수를 통해 해당인덱스의 항목을 제거할 수 있다.

``` python
data_list.pop(5) #인덱스 5에 해당하는 항목 제거
```

- remove(항목 값) 함수를 통해 해당 항목값을 지닌 첫번째 항목을 제거할 수 있다

  ``` python
  data_list.pop(100)
  ```

- clear() 함수를 통해 모든 항목을 제거하여 빈 리스트 객체를 생성할 수 있다.
  - del 명령과 범위 연산자만 이용해 모든 항목을 제거할 수도 있다.
  - del data_list[:]

#### 리스트 항목 확인

- '항목값 in 리스트객체' 명령을 사용하면 리스트 객체에 해당 항목이 있는지 검사한다.
  - True와 False를 반환한다. 
- '항목값 not in 리스트객체' 명령은 리스트 객체에 해당 항목이 없는지 검사한다.
- count()함수 : 인자로 전달된 항목의 개수 확인 가능

#### 리스트와 for문(리스트 객체의 개별 항목 접근법)

``` python
data_list = list(range(0 11. 2)) # 범위 : 0 ~ 10, 간격 : 2

for item in data_list : #리스트 항목을 반복해서 변수 item에 저장
    print("{0}".format(item), end=" ")# 반복해서 저장시 변수 item에 저장되어 있는 항목 값과 공백문자를 함께 출력한다.
    
print()

for idx, item in enumerate(data_list): # 데이터 리스트를 enumeration 객체로 변환하고 인덱스와 항목정보를 매 반복마다 변수 idx와 item에 저장
    print("data_list[{0}] => {1}".format(idx, item))
    
# 출력결과
'''
0 2 4 6 8 10
data_list[0] => 0
data_list[1] => 2
data_list[2] => 4
data_list[3] => 6
data_list[4] => 8
data_list[5] => 10
'''
```





## 리스트 내포의 특징

### 리스트 내포

- 반복 가능한 자료형의 경우 리터럴 안에서 for 문을 사용하면 내포 기능 사용 가능

  ``` python
  data_list1 = [1, 2, 3, 4, 5]
  
  data_list3 = [item for item in data_list1]
  print("data_list3: {0} {1}".format(type(data_list3), data_list3))
  # 리스트 내포 기능을 사용하여 data_list1과 동일한항목을 가진 data_list3 리스트 객체를 생성한다.
  
  data_list4 = []
  for item in data_list1:
      if item % 2 == 1:
          data_list4.append(item)
  print("data_list4: {0} {1}".format(type(data_list4), data_list4))
  
  data_list5 = [item for item in data_list1 if item % 2 == 1 ]
  print("data_list5: {0} {1}".format(type(data_list5), data_list5))
  
  '''
  출력결과
  data_list4: <class 'list'>[1, 3, 5]
  data_list5: <class 'list'>[1, 3, 5]
  '''
  ```

- 리스트 내포도 for 문의 중첩 구조 사용이 가능하다.

  ``` python
  data_list8 = [x * y for x in data_list1 if x % 2 == 1 
               		for y in data_list1 if y % 2 == 0]
  ```

- 문자열도 리스트 내포 구조를 사용해 간단히 새로운 리스트 객체로 변환이 가능하다.

  ``` python
  data_str = "Hello, Python!"
  data_list9 = [item.lower() for item in data_str] # for문에서 문자열을 사용하면 각각의 문자가 항목이 된다.
  print("data_list9: {0} {1}".format(type(data_list9), data_list9))
  ```

  

## 튜플의 생성 및 조작법

### 튜플

- **중괄호()**안에 ** 서로 다른 자료형의 값을** 콤마(,)로 구분해 **하나 이상 저장**할 수 있는 컬렉션 자료형이다.
- 개별 항목은 0부터 시작하는 인덱스를 이용해 접근할 수 있다.
- **한 번 저장된 항목은 변경할 수 없다는 특징을 지닌다.** 이 점이 리스트와의 차이점이다.
- 문자열을 튜플로 저장하면 개별 문자를 원소로 하는 튜플 객체를 생성한다. 

### 튜플 조작법

#### 튜플 항목 접근

- 각 항목은 인덱스를 통해 접근할 수 있다.
- 항목의 개수가 N이면 마지막 항목은 N-1로 접근할 수 있다.
- 상대적인 인덱스를 통해서도 튜플의 각 항목에 접근할 수 있다.
  - ex) data_tuple[-1], 마지막 항목을 뜻한다.
- index(항목 값)을 통해 해당 항목의 값이 들어 있는 첫 번째 위치의 인덱스를 반환한다. 

#### 튜플 기본 연산

- '+' 연산자를 이용해 두 항목을 연결한 새로운 튜플을 생성할 수 있다.
- '*' 연산자를 이용해 튜플을 여러 번 연결하는 새로운 튜플을 생성할 수 있다.

#### 튜플 항목 확인

- '항목값 in 튜플 객체' 명령을 사용하면 튜플객체에 해당 항목이 있는지 검사한다.
  - True와 False를 반환한다. 
- '항목값 not in 튜플객체' 명령은 튜플객체에 해당 항목이 없는지 검사한다.
- count()함수 : 인자로 전달된 항목의 개수 확인 가능

#### 



## 튜플 내포의 특징

``` python
data_tuple1 = (1, 2, 3, 4, 5)

data_tuple3 = tuple(item for item in data_tuple1 if item % 2 == 1)
print("data_tuple3 : {0} {1}".format(type(data_tuple3), data_tuple3))
# data_tuple1의 항목 중 2로 나누었을 때 나머지가 1인 홀수 항목을 가진 data_tuple3 튜플 객체를 생성한다.
# 출력결과, data_tuple3: <class 'tuple'> (1, 3, 5)

data_tuple5 = tuple(x * y for x in data_tuple1 if x % 2 == 1 
                   	  	  for y in data_tuple1 if y % 2 == 0)
print("data_tuple5 : {0} {1}".format(type(data_tuple5), data_tuple5))
# 출력결과, data_tuple5: <class 'tuple'> (2, 4, 6, 12, 10, 20)
```

















































