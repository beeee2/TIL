# 내장함수

프로그래밍시 검증된 함수를 활용함으로써 생산성 및 프로그램의 품질을 향상시킨다. 그렇기에 프로그램을 만들기 전 나에게 필요한 함수가 있는지 **API(Application Programming Interface)문서**를 찾아보는 것이 좋다. 



파이썬은 '수치형 데이터 조작을 위한 함수', '집합과 원소 사이의 관계를 다루는 함수', '각종 변환 함수' 등 다양한 내장함수를 제공한다. 

---



## 수치 연산 함수 

#### abs() 함수

- 인자로 숫자를 전달하면 그 **숫자의 절대값을 반환**하는 함수

#### divmod() 함수

- 첫 번째 인자를 두 번째 인자로 나눴을 때의 몫과 나머지를 튜플 객체로 반환하는 함수

- 예시

  ``` py
  val1, val2 = 9, 5
  result_tuple = divmod(val1, val2)
  # 몫과 나머지를 튜플 객체로 반환해 변수 result_tuple에 저장한다.
  
  print("divmod({0}, {1})=>몫:{2}, 나머지:{3}".format(val1, val2, *result_tuple))
  
  [결과]
  divmod(9, 5) => 몫 : 1, 나머지 : 4
  ```

#### pow()

- 첫 번째로 전달된 인자 값에 대해 두 번째로 전달된 인자 값으로 **제곱한 결과를 반환**하는 함수



---



## 시퀀스형/반복 가능한 자료형을 다루는 함수

#### all()

- 반복 가능한 자료형인 List, Tuple, Set, dictionary, 문자열 등을 인자로 전달하여 **항목 모두가 True로 평가되면 True를 반환**하고, **False로 평가되는 항목이 하나라도 있으면 False를 반환**하는 함수
- 예시

``` python
val = [True, True, True]
print("all({0}) => {1}".format(val, all(val)))

val = [10, 20, 30]
print("all({0}) => {1}".format(val, all(val)))

val = [10, 20, 0]
print("all({0}) => {1}".format(val, all(val)))

val = [10, 20, ""]
print("all({0}) => {1}".format(val, all(val)))

val = [10, 20, False]
print("all({0}) => {1}".format(val, all(val)))

val = [10, 20, None]
print("all({0}) => {1}".format(val, all(val)))

"""
[결과]
all([True, True, True]) => True
all([10, 20, 30]) => True
all([10, 20, 0]) => False
all([10, 20, ""]) => False
all([10, 20, False]) => False
all([10, 20, None]) => False

"""
```



#### any()

- 반복 가능한 자료형인 List, Tuple, Set, dictionary, 문자열 등을 인자로 전달하여 항목 **모두가 False로 평가되면 False로 반환하고, True로 평가되는 항목이 하나라도 있으면 True를 반환**하는 함수



#### enumerate()

- List, Tuple, 문자열과 같은 시퀀스형을 입력받아 **인덱스를 포함하는 튜플 객체를 항목으로 구성하는 enumertate 객체를 반환**하는 함수
- 시퀀스 자료형은 **순서**를 가지고 나열되어 있는 객체를 의미한다.

- 예시

``` python
data_list = [10, 20, 30, 40, 50]
#data_list에 리스트 객체를 저장한다.

for idx, val in enumerate(data_list):
    print("data_list[{0}]: {1}".format(idx, val))
    # for문에서 먼저 data_list를 enumerate 객체로 변환한다.
    # 이를 통해 매 반복마다 해당 인덱스와 항목을 
    # 변수 idx와 val 에 저장하여 이 값을 출력한다.
    
print("-" * 25)

for ojb in enumerate(data_list):
    print("{0}: {1}, {2}".format(type(obj), ojb[0], obj[1]))
    # data_list를 enumerate 객체로 변환
    # 변수 obj: 튜플 객체로 첫번째 항목에 접근애 인덱스를, 두 번째 항목에 접근해 값을 출력한다.
    
print("-" * 25)

for obj in enumerate(data_list):
    print("{0}: {1}, {2}".format(type(obj), *obj))
    # 변수 obj: 튜플객체로 인덱스와 값을 출력한다.

```



#### filter()

- 조건에 해당하는 항목을 걸러내는 함수

- 첫 번째 매개변수는 전달받은 인자에 대해 **True 또는 False 반환**한다. 두 번째 매개변수에는 **반복가능한 자료형**을 인자로 넣어야 한다.

  - 이 때 전달된 반복가능한 자료형의 인자가 첫 번째 매개변수의 인자로 전달된다. 

  ``` python
  def iseven(num):
      return num % 2 == 0
  
  numbers = [1, 2, 3, 4, 5, 6,7, 8, 9, 10]
  
  ret_val = filter(iseven, numbers)
  # ret_val = filter(lambda n: n % 2 == 0, numbers)
  print("{0}".format(type(ret_val)))
  print("{0}".format(list(ret_val)))
  
  [결과]
  <class 'filter'> # 필터 객체 타입 반환
  [2, 4, 6, 8, 10] # 필터 객체를 리스트로 변환
  
  
  ```



### list(), tuple(), set(), dict() 함수 알아보기

이 네개의 함수는 반복 가능한 자료형을 인자로 전달 받아 각각 리스트, 튜플, 섹, 딕셔너리로 변환해 반환하는 함수이다.

```python
data_str = "Hello"

data_list = list(data_str)
print("list('{0}') => {1} {2}".format(data_str, type(data_list), data_list))
# 출력결과 list('Hello') => <class 'list'>['H', 'e', 'l', 'l', 'o']

data_tuple = tuple(data_list)
print("list('{0}') => {1} {2}".format(data_list, type(data_tuple), data_tuple))
# 출력결과 list(['H', 'e', 'l', 'l', 'o']) => <class 'tuple'>('H', 'e', 'l', 'l', 'o')

data_set = set(data_tuple)
print("list('{0}') => {1} {2}".format(data_tuple, type(data_set), data_set))
# 출력결과 list(('H', 'e', 'l', 'l', 'o')) => <class 'set'>{'H', 'e', 'l', 'o'}
# 중복제거, 유일값, 순서는 의미가 없다.

data_dict = dict(enumerate(data_set))
print("list('{0}') => {1} {2}".format(data_set, type(data_dict), data_dict))
# 인덱스와 값으로 구성된 tuple을 항목으로 하는 enumerate 객체 생성
# 출력결과 list({'H', 'e', 'l', 'o'}) => <class 'dict'>{'0':'H', '1':'e', '2':'l', '3':'o'}
```



### map()

두번째 인자로 반복 가능한 자료형을 전달 받아 **자료형의 각 항목에 대해 첫 번째 인자로 전달 받은 함수를 적용한 결과를 맵 객체로 반환**하는 함수

``` python
data_list = list("abcdef")

result = list(map(lammda x: x.upper(), data_list))
# data_list 객체의 항목에 대해 대문자로 변환한 항목을 가진 map 객체를 반환한다.
print("list(map(lambda x: x.upper(), {0})) => {1} {2}".format(data_list, type(result), result))
# 결과
# list(map(lambda x: x.upper(), ['a', 'b', 'c', 'd', 'e', 'f'])) => <class 'list'>['A', 'B', 'C', 'D', 'E', 'F'] 
```



### max(), min()

- max()는 반복 가능한 자료형을 인자로 전달받아 항목 중 **가장 큰 값을 반환**하는 함수
- min()는 반복 가능한 자료형을 인자로 전달받아 항목 중 **가장 작은 값을 반환**하는 함수



### range()

첫 번째 인자로 **전달된 시작 값**, 두 번째 인자로 **전달된 종료 값**, 세 번째 인자로 **전달된 증감치**를 통해 **시퀀스형 객체를 생성**하는 함수이다.

이 때, 종료 값으로 사용된 두 번째 인자의 값은 포함되지 않는다.

``` python
data_list1 = list(range(0, 10, 1))
data_list2 = list(range(0, 10))
data_list3 = list(range(10))
# 생략된 첫 번째 매개변수의 기본 값은 0이고 세 번째 매개변수의 기본 값은 1로 설정된다.
# 위 data_list1~3을 출력하면 동일한 결과를 얻을 수 있다. [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```



### sorted()

반복 가능한 자료형을 인자로 전달받아 항목들로부터 **정렬된 리스트를 생성해 반환**하는 함수다. 

``` python
data_list = [3, 8, 12, 2, 5, 11]

asc_result = sorted(data_list)
# 오름차순으로 정렬된 리스트 객체를 생성해 반환한다.

print("{0} {1}".format(type(data_list), data_list))
print("{0} {1}".format(type(asc_result), asc_result))

print("-" * 35)

desc_result = list(reversed(asc_result))
# 내림차순의 리스트 객체 생성

print("{0} {1}".format(type(data_list), data_list))
print("{0} {1}".format(type(asc_result), asc_result))
print("{0} {1}".format(type(desc_result), desc_result))

# 출력결과
'''
<class 'list'>[3, 8, 12, 2, 5, 11]
<class 'list'>[2, 3, 5, 8, 11, 12]
----------------------------------
<class 'list'>[3, 8, 12, 2, 5, 11]
<class 'list'>[2, 3, 5, 8, 11, 12]
<class 'list'>[12, 11, 8, 5, 3, 2]
'''
```



### zip()

둘 이상의 반복 가능한 자료형을 인자로 전달받아, **동일 위치의 항목을 묶어 튜플을 항목으로 구성하는 zip 객체를 생성**하는 함수

이 때 인자로 전달된 객체는 **동일 자료형**이면서, **항목의 개수가 같아야 한다.**

``` python
data_list = [1, 2, 3]
data_list = [4, 5, 6]
```

