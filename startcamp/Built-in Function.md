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

