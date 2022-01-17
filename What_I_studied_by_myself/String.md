# 문자열

컴퓨터 안의 워드 엑셀등의 각종 파일과 웹으로 수집된 문서들로부터 필요한 데이터를 얻기 위해서는 **전처리 과정**이 필요하다.

전처리과정은 **불필요한 데이터를 삭제하고 추출하기**위해 **문자열 찾기, 문자열 조작, 문자열 치환등을 활용**한다.



## 문자열 연산

### 문자열이 제공하는 연산

#### 문자열의 연결

- 문자열 연결 연산자(+)를 이용해 연산할 수 있다.
- str.format() 함수를 이용해 위치 지시자에 지정한 값으로 변경할 수 있다.

#### 문자열의 반복

- 반복하고자 하는 문자열 + 문자열 반복 연산자(*) + 반복 횟수

  ``` python 
  print("-" * 13, end="")
  # "-"를 13번 반복한 문자열을 생성하며 공백문자열로 줄바꿈을 없앤다.
  ```

   

#### 문자의 선택

- 인덱스로 선택할 수 있다. 

#### 문자열의 범위 선택

- 인덱스를 사용한다. [시작인덱스 : 종료인덱스]



## 문자열 함수

- len(문자열) : 문자열의 길이를 반환한다.

- find() : 특정 문자열을 찾을 수 있다. 
  - find () 함수는 해당 문자열에서 지정된 값을 찾고 시작 인덱스를 반환한다. 못 찾을 경우 -1을 반환한다.

- rfind() : 특정 문자열을 찾는다. 문자열을 찾을 경우 시작 인덱스를 반환하고, 못 찾을 경우 -1을 반환한다.
  - find() 함수는 문자열을 찾을 때 왼쪽에서 오른쪽으로(처음에서 끝으로) 찾으며
  - rfind() 함수는 오른쪽에서 왼쪽으로(끝에서 처음으로) 향하며 찾는다. 
- index() : 문자열을 찾는다. 문자열을 못 찾을 경우 Value Error를 발생시킨다. 



#### 문자열의 삽입

- join 함수 : 문자열 삽입합수

  ``` python
  data_str = "가나다라마바사아자차카타파하"
  comma_space = ", "
  
  output = comma_space.join(data_str) 
  print(output)
  # comma_space에 저장된 값을 구분 문자열로 data_str의 각 항목 사이에 삽입한다.
  # 출력결과
  # 가, 나, 다, 라, 마, 바, 사, 아, 자, 차, 카, 타, 파, 하
  
  ```

#### 대소문자 바꾸기

- capitalize, lower, upper : 대소문자 변경 관련 함수

  ``` python
  data_str = "better tomorrow"
  
  data_str = data_str.capitalize() # 첫 번째 문자를 대문자로 하는 새로운 문자열을 반환한다.
  print("'{0}'".format(data_str))
  # 출력결과
  # 'Better tomorrow'
  
  data_str = data_str.lower() # 모든 문자를 소문자로 한 새로운 문자열을 반환한다.
  print(data_str)
  # better tomorrow
  
  data_str = data_str.upper() # 모든 문자를 대문자로 한 새로운 문자열을 반환한다.
  print(data_str)
  # BETTER TOMORROW
  ```

#### 공백제거하기

- lstrip, rstrip, strip : 왼쪽, 오른쪽, 양쪽 공백 제거 함수

  ``` python
  data_str = "  홍 길동  "
  data_str = data_str.lstrip("")
  print(data_str) # " 홍 길동  "
  
  data_str = "___홍 길동_____ "
  data_str = data_str.rstrip("_ ") # 인자로 전달된 문자열을 문자열의 오른쪽에서 제거한다.
  print(data_str)
  # 출력결과 : '___홍 길동'
  
  data_str = " 0?홍  길동 _#    "
  data_str = data_str.strip(" 0?_#")
  print(data_str)
  # 출력결과 : '홍  길동'
  
  ```

#### 문자열 교체

- replace() : 

  - 찾을 문자열과 교체 문자열을 인자로 사용해 교체한다.
  - 첫 번째 인자 - 찾을 문자열, 두 번째 인자 - 교체할 문자열 

  ``` python
  data_str = "10....20....30....40....50"
  
  data_str = data_str.replace("." * 4, "\t")
  print(data_str)
  '''
  출력결과
  10	20	30	40	50
  '''
  ```

#### 문자열 자르기

- split() : 전달된 인자로 문자열을 잘라 이를 항목으로 갖는 리스트를 생성한다.

  ``` python
  data_str = "10, 20, 30, 40, 50"
  
  data_str = data_str.replace(" ", "")
  print(data_str)
  # 10,20,30,40,50
  
  data_list = data_str.split(",")
  for val in data_list:
      print(val)
  '''
  10
  20
  30
  40
  50
  '''
  ```



