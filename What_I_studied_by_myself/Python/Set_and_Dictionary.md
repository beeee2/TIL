# 셋, 딕셔너리

다양한 데이터 중 중복되지 않은 유일한 정보가 필요할 때가 있다. 

중요한 식별자를 Key data라고 한다. 이 때 키 데이터는 중복을 허용해서는 안된다. 

파이썬에서는 중복되지 않는 데이터를 만들기 위해 셋이라는 자료구조를 사용한다.

또한, 유일성을 가진 키데이터와 관련데이터를 연결한 사전 구조를 닮았다고 하여 이름이 붙여진 딕셔너리라는 자료구조를 제공한다.



- 셋(Set)과 딕셔너리(Dictionary)는 파이썬에서 제공하는 **반복형 자료구조**이며 **데이터의 중복을 허용하지 않는다.**

## 셋 생성 및 조작법

- 셋은 중괄호{} 안에 **서로 다른 자료형의 유일한 값**을 콤마(,) 로 구분해 **하나 이상 저장할 수 있는 컬렉션 자료형**중의 하나이다.
- 인덱스를 제공하지 않는다.
- 순서의 개념이 없다.
- 중복을 허용하지 않는다.

### 셋의 생성

- 셋 객체의 리터럴은 중괄호 {} 안에 항목을 콤마(,)로 구분해 기술한다.

  ``` python
  data_set = {10, 20, '파이썬', '파이썬'}
  
  print(data_set)
  # 출력결과 {'파이썬', 10, 20}
  # 중복을 허용하지 않아 문자열 "파이썬"이 하나만 저장된다.
  
  data_set = set(range(10, 21, 2))
  print(data_set)
  # 출력결과, {10, 12, 14, 16, 18, 20}
  
  data_str = "Better Tomorrow"
  data_set = set(data_str) # 개별 문자를 원소로 하는 셋 객체를 생성한다.
  print(data_set)
  # 출력결과, {' ', 'o', 'w', 'T','m','t','e','r','B'} 
  # 정해진 순서 없이 출력된다. 
  # 중복된 문자는 한 번만 저장된다.
  ```

### 셋 조작법

#### 셋 기본 연산

- 교집합 & (intersection)
- 합집합 | (union)
- 차집합 - (difference)

#### 셋 항목 추가

- add() 함수로 항목을 추가한다.
- update({}) 함수로 항목을 추가할 수 있다.

#### 셋 항목 제거

- remove(항목값) 함수를 이용해 해당 항목을 제거할 수 있다. 
- pop() 함수를 통해 첫 번째 항목을 제거할 수 있다.
- clear() 함수로 모든 객체를 제거할 수 있다.
  - 이 때 {}는 딕셔너리의 리터럴이기 때문에, 비어있는 셋은 set()으로 표시된다.

#### 셋 항목 확인

- 항목값 in 셋객체 : 셋 객체에 해당 항목이 있는지 검사할 수 있다.
  - True or False를 반환한다.
- 항목값 not in 셋객체 : 셋 객체에 해당 항목이 없는지 검사한다. 
- a.issuperset(b) : a가 b를 전부 포함하는 집합인지 확인한다. 
- a.ssubset(b) : a가 b에 전부 포함되는 집합인지 확인한다. 

#### for 문을 이용한 셋 항목 접근



## 셋 내포의 특징

``` python
data_set1 = {1, 2, 3, 4, 5}

data_set2 = {item for item in data_set1} 
# 반복가능한 자료형의 경우 해당 리터럴 안에서 for 문을 사용하면 내포기능을 사용할 수 있다.
# 셋 내포 기능을 이용하여 data_set1과 동일한 항목을 지닌 data_set2 셋 객체를 생성한다.

data_set3 = {item for item in data_set1 if item % 2 == 1}
# data_set1의 항목을 2로 나누었을 때 나머지가 1인 홀수 항목을 data_set3 셋 객체로 생성한다.
print("data_set3: {0} {1}".format(type(data_set3), data_set3))
# data_set3: <class 'set'>{1, 3, 5}

data_set5 = {x * y for x in data_set1 if x % 2 == 1
            		for y in data_set1 if y % 2 == 0}
print("data_set5: {0} {1}".format(type(data_set5), data_set5))
# 셋 내포는 for 문의 중첩 구조 사용이 가능하다.
# if 조건문을 추가해 조건을 만족하는 항목만 선택해 연산의 결과로 항목을 만들 수 잇다.
```



### 리스트, 튜플, 셋의 변화

``` python
data_str = "Hello"

data_list = list(data_str)
print("{0} => {1} : {2}".format(type(data_str), type(data_list), data_list))

data_tuple = tuple(data_list)
print("{0} => {1} : {2}".format(type(data_list), type(data_tuple), data_tuple))

data_set = set(data_tuple)
print("{0} => {1} : {2}".format(type(data_tuple), type(data_set), data_set))

data_list = list(data_set)
print("{0} => {1} : {2}".format(type(data_set), type(data_list), data_list))

'''
출력결과
<class 'str'> => <class 'list'> : ['H', 'e', 'l', 'l', 'o']
<class 'list'> => <class 'tuple'> : ('H', 'e', 'l', 'l', 'o')
<class 'tuple'> => <class 'set'> : {'H', 'e', 'l', 'o'}
<class 'set'> => <class 'list'> : ['H', 'e' , 'l', 'o']
'''
```





## 딕셔너리 생성 및 조작법

### 딕셔너리

- 중괄호{} 안에 **키 : 값의 형식을 가진 유일한 데이터**를 콤마(,)로 구분해 **하나 이상 저장할 수 있는 컬렉션 자료형** 중의하나
- dict(키=값) : **dict 생성자** 함수에 키와 값을 적어 딕셔너리 객체를 생성할 수 있다.
  - 이 때 **'키=값' 형식의 매개변수 목록에서 키를 문자열로 작성하지 않도록 주의해야 한다.**
- 튜플 객체를 dict 함수의 인자로 전달해 딕셔너리 객체를 생성할 수 있다.
- 리스트 객체를 dict 함수의 인자로 전달해 딕셔너리 객체를 생성할 수 있다.
- 셋 객체를 dict 함수의 인자로 전달해 딕셔너리 객체를 생성할 수 있다.
- 인덱스를 제공하지 않는다.
- 순서의 개념이 없다.
- 중복을 허용하지 않는다.

### 딕셔너리 조작법

#### 딕셔너리 항목 추가

- 객체 이름[중복되지 않은 키] = 값
- 객체 이름.update({'키1' : 값1, '키2' : 값2})
  - update() 함수에 딕셔너리 객체를 전달하면 새로운 항목으로 추가된다.

#### 딕셔너리 항목 변경

- 객체 이름[중복되는 키] = 값
- update({'키1' : 값1, '키2' : 값2}) 키가 동일할 때 기존 항목을 변경한다.

#### 딕셔너리 항목 제거

- del 명령으로 데이터를 삭제 할 수 있다.	
  - del 객체이름[키]
- 객체이름.pop(키) : pop함수를 호출해 데이터를 삭제한다.
- 객체이름.clear() : 모든 항목이 삭제되며, {} 빈 딕셔너리 객체 리터럴을 출력한다.

#### 딕셔너리 항목 확인

- "키" in 객체이름 : 해당 키가 딕셔너리 항목에 있는지 검사
- "키" not in 객체이름 : 해당 키가 딕셔너리 항목에 없는 지 검사 

#### for 문을 이용한 딕셔너리 항목 접근

``` python
data_dic1 = {
    "홍길동" : 20,,
    "이순신" : 45,
    "강감찬" : 35
} 

print("{0} {1}".format(type(data_dict1.items()), data_dict1.items())) # 튜플로 구성되어 출력된다.
# <class 'dict_items'> dict_items([('홍길동', 20), ('이순신', 45), ('강감찬', 35)])
print("{0} {1}".format(type(data_dict1.keys()), data_dict1.keys())) # 문자열로 구성되어 출력된다.
# <class 'dict_keys'> dict_keys(['홍길동', '이순신', '강감찬'])
print("{0} {1}".format(type(data_dict1.values()), data_dict1.values())) # 정수로 구성되어 출력된다.
# <class 'dict_values'> dict_keys([20, 45, 351])

```





## 딕셔너리 내포의 특징

``` python
data_dict1 = {
    '홍길동' : 20,
    '이순신' : 45,
    '강감찬' : 35
} 

data_set1 = {item for item in data_dict1.items()} # 반복 가능한 자료형의 경우 for 문으로 내포기능 사용
print("data_set1: {0} {1}".format(type(data_set1), data_set1))
# 출력결과
# data_set1 : <class 'set'> {('홍길동', 20), ('이순신', 45), ('강감찬', 35)}

data_dict2 = {key : data_dict1[key] for key in data_dict1}
# 딕셔너리 내포 기능으로 data_dict1의 항목을 가진 data_dict2 딕셔너리 객체를 생성

data_dict4 = {item[0] : item[1] for item in data_dict1.items()}
# data_dict1.items() 함수 호출에 의해 반환된 dict_items 객체의 튜플 객체 항목에서, 
# 키 : 값으로 변환된 항목을 갖는 data_dict4 딕셔너리 객체를 생성한다.

data_dict5 = {key : value for key, value in data_dict1.items()}
# dict_items 객체의 튜플 객체 항목을 각각 변수 key, vaule에 저장하고
# key : value 형식의 쌍을 항목으로 가진 data_dict5 딕셔너리 객체를 생성한다.

```

