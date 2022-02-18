# 	Algorithm - String

## 목차

#### ☑ 문자열

#### ☑ 패턴 매칭

#### ☑ 문자열 암호화

#### ☑ 문자열 압축

#### ☑ 문제 풀이 연습



---

## 문자의 표현

### 컴퓨터에서의 문자 표현

- 글자 A를 메모리에 저장하기 위해서는 각 문자에 대응되는 숫자를 정해놓고 이것을 메모리에 저장한다.
- 영어의 대소문자를 합치면 52이므로 6비트(64)면 모두 표현할 수 있다.
- 이를 코드 체계라고 한다.
  - 000000 > 'a', 000001 > 'b'

- 지역별로 다른 코드체계로 인한 혼동을 피하기 위해, 1976년 미국에서 ASCII(American Standard Code for Information Interchange)라는 문자 인고코 표준이 제정되었다.
- ASCII는 7bit 인코딩으로 128문자를 표현하며 33개의 출력 불가능한 제어 문자들과 공백을 비롯한 95개의 출력 가능한 문자들로 이루어져 있다.
  - 출력 가능한 아스키 문자는 32~126 구간이다. 
  - 대문자 A는 65이며, 소문자 a는 97이다.

#### 확장 아스키는 표준 문자 이외의 악센트 문자, 도형 문자, 특수 문자, 특수 기호 등 부가적인 문자를 128개 추가할 수 있게 하는 부호이다.

- 표준 아스키는 7bit를 사용하여 문자를 표현하는 데 비해 확장 아스키는 1B내의 8bit를 모두 사용함으로써 추가적인 문자를 표현할 수 있다.
- 컴퓨터 생산자와 소프트웨어 개발자가 여러 가지 다양한 문자에 할당할 수 있도록 하고 있다. 이렇게 할당된 확장 부호는 표준 아스키와 달리 서로 다른 프로그램이나 컴퓨터 사이에 교환되지 못한다.
- 그러므로 표준 아스키는 마이크로컴퓨터 하드웨어 및 소프트웨어 사이에서 세계적으로 통용되는 데 비해, 확장 아스키는 프로그램이나 컴퓨터 또는 프린터가 그것을 해독할 수 있도록 설계되어 있어야만 올바로 해독될 수 있다.

##### 오늘날 대부분의 컴퓨터는 문자를 읽고 쓰는데 ASCII 형식을 사용한다.

##### 각 국가들은 ASCII로 표현하기 어려운 자국의 문자를 표현하기 위해 코드체계를 별도로 만들어 사용하게 되었다. 인터넷이 저 세계로 발전하며 국가간 정보를 주고 받을 때 다시 분제가 발생하였다 자국의 코드체계를 타 국가가 가지고 있지 않으면 정보를 잘못 해석할 수 밖에 없었다. 그래서 다국어 처리를 위해 표준을 마련했다. 이를 유니코드라고 한다.

### 유니코드도 다시 Character Set으로 분류된다.

- UCS-2(Universal Character Set2)
- UCS-4(Universal Character Set4)
- 유니코드를 저장하는 변수의 크기를 정의(2bite 혹은 4바이트를 통해 문자 표현할 수 있게끔)
- 그러나, 바이트 순서에 대해서 표준화하지 못했다
- 다시 말해 파일을 인식 시 이 파일이 UCS-2, UCS-4인지 인식하고 각 경우를 구분해서 모두 다르게 구현해야 하는 문제가 발생했다. 그래서 유니코드의 적당한 외부 인코딩이 필요하게 되었다.

### big-endian, little-endian

- 메모리는 바이트 단위로 접근한다. 주소가 저장되는 최소 단위는 바이트이다.

- 메모리는 주소를 가진다.

- little-endian은 낮은 자릿수를 빠른 주소에 저장하는 방법
- big-endian은 낮은 자릿수를 빠른 주소에 저장하는 방법 

### 유니코드 인코딩(UTF : Unicode Transformation Format)

- UTF-8 (in web)
  - 가변길이로 MIN : 8bit, MAX : 32bit
  - 기본적으로 4byte이다.
- UTF-16(in windows, java)
  - MIN : 16bit, MAX: 32bit(기본적으로 2 Byte * 2)
- UTF-32(in unix)
  - MIN : 32bit, MAX : 32bit(4 Byte * 1)

### Python 인코딩

- 2.x 버전 : ASCII -> #-*- coding:utf-8 -*-(첫 줄에 명시)
- 3.x 버전 : 유니코드 UTF-8 -> 생략가능
- 다른 인코딩 방식으로 처리 시 첫 줄에 위 항목에서 원하는 인코딩 방식을 지정해주면 된다.



### 다음 두 코드의 차이 이해하기

``` python
s1 = list(input())
s2 = input()
```

### strlen() 함수 만들어보기 

- def strlen(a) : '\0'을 만나면 '\0' 을 제외한 글자수 리턴

- #while 써서 함수 완성

- a = ['a', 'b', 'c', 'd']

- print(strlen(a))

  ``` python
  def strlen(lis):
      cnt = 0
      lis.reverse()
      while True:
          lis.pop()
          cnt += 1
          if lis[0] == lis[-1]:
              return cnt
              break
  
  list_ = ['a', 'c', 'b', '\0']
  print(strlen(list_))
  ```

​	

```python
#교수님 풀이
def mystrlen(s):
    i = 0
    while s[i] != '\0':
        i += 1
    return i

a = ['a', 'c', 'b', '\0']
print(mystrlen(a))
```







---



## 문자열

Python에서의 문자열 처리

- char 타입 없음
- 텍스트 데이터의 취급 방법이 통일되어 있다.
- 문자열 기호
  - 홑따옴표, 쌍따옴표, 홑따옴표3개, 쌍따옴표 3개
  - '+' 연결을 의미한다. 문자열 + 문자열은 서로 이어 붙는다.
  - ' * ' 반복을 의미한다. 문자열 * 수는 수만큼 문자열이 반복된다.



### C와 Java의 String 처리의 기본적인 차이점

- c는 아스키 코드로 저장한다.
- java는 유니코드(UTF16, 2byte)로 저장한다.
- 파이썬은 유니코드(UTF-8)로 저장한다.



#### 참고, s1과 나머지 문자열을 ==, is로 비교한 결과를 확인해보세요.

``` python
s1 = 'abc'
s2 = 'abc'
s3 = 'def'
s4 = s1
s5 = s1[:2] + 'c'

# s1 == s2, True
# s1 is s2, True
# s1 == s4, True
# s1 is s4, True
# s1 == s5, True
# s1 is s5, False

# == 는 내용을 비교하고 is는 위치참조주소를 비교한다.
```

#### 문자열 비교함수

``` python
a = 'abc'
b = 'ab'
c = 'de'
d = 'Abc'

print(a > b) # True
print(a > d) # True
print(a == d) # False
```

위를 참고하여 작성해보자.

문자열이 같으면 0을 리턴하고 s1이 s2보다 사전 순서상 앞서면 음수 혹은 -1리턴

s1이 s2보다 순서상 나중이면 양수 혹은 1리턴

``` python
def my_strcmp(s1, s2):
    if s1<s2:
        return -1
    elif s1>s2:
        return 1
    else:
        return 0
```

#### int()와 같은 atoi() 함수 만들기

``` python
def atoi(s):
    i = 0
    for x in s:
        i = i * 10 + ord(x) - ord('0')
    return i

s = '123'
a = atoi(s)
print(a)
```

#### str() 함수를 사용하지 않고, itoa() 구현하기

- 연습문제 참고





---

## 패턴매칭

### 패턴매칭에 사용되는 알고리즘들

- 고지식한 패턴 검색 알고리즘
- 카프-라빈 알고리즘
- KMP 알고리즘
- 보이어-무어 알고리즘



### 고지식한 알고리즘(Brute Force)

- 본문 문자열을 처음부터 끝까지 차례대로 순회하면서 패턴 내의 문자들을 일일이 비교하는 방식으로 동작한다.

  ``` python
  pattern = 'is'
  total = 'This is a book~!'
  patter_len = len(pattern)
  total_len = len(total)
  
  def BruteForce(pattern, total):
      total_idx = 0 # total의 인덱스
      pattern_idx = 0 # ppattern의 인덱스
      while pattern_idx < patter_len and total_idx < total_len :
          if total[total_idx] != pattern[pattern_idx]:
              total_idx = total_idx - pattern_idx
              pattern_idx = -1
          total_idx += 1
          pattern_idx += 1
      if pattern_idx == patter_len:
          return total_idx - patter_len #검색성공
      else:
          return -1 #검색실패
  print(BruteForce(pattern, total))
  ```

- 고지식한 패턴 검색 알고리즘의 시간 복잡도

  - 최악의 경우 시간 복잡도는 텍스트의 모든 위치에서 패턴을 비교해야 하므로 O(MN)이 된다.
  - 예에서는 최악의 경우 10,000*80 = 800,000 번의 비교가 일어난다.
  - 비교횟수를 줄일 수 있는 방법은 없는가?





## KMP 알고리즘

- 접미어 중 가장 많이 겹치는, 긴 접두어를 LPS 리스트로 둔다.
- 패턴을 가지고 LPS Table을 만들어야 한다.





---





## 추가기록

### 중요한 것 

- **DAT(Direct Address table) 자료구조**
- **Direct 배열(방향배열을 이용한 코드)**
- **Bs(binary search) - O (log n)**
- **시간 복잡도**
- **Greedy (개념이해) - 동전 교환 예시**
- 버블sort, 선택정렬
- count sort
- Pattern 찾기, 입력받기
- 비트연산 
- kmp 문자열( 접두사 접미사를 이용한 문자열 매칭)

아래는 코딩 테스트에서 자주 다루는 것

- sliding window 알고리즘
- two pointer 알고리즘