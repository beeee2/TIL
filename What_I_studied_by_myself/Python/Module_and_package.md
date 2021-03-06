# 모듈과 패키지

파이썬에서는 파일로 모듈이라는 단위를 관리하며 모듈을 이용해 코드를 공개하고 배포할 수 있다.

**모듈**을 통해 **생산성과 재사용성을 높일 수 있다.**



## 표준 모듈과 활용

### 표준 모듈

- 파이썬은 표준 모듈이라고 하는 내장된 모듈을 제공한다. 
- **각기 목적에 맞게 설계**되어 있고 다양한 함수 클래스 등을 제공하며, 별도의 추가 설치 과정없이 **import문으로 로딩해서 사용**할 수 있다.
- 이름으로 모듈을 참조해서 해당 모듈이 가진 함수를 활용할 수 있다.
- 예시
  - math 모듈, 유용한 각종 수학 함수와 미리 정의된 값들을 포함한다.
    - math.radians() : 각도를 인자로 전달하면 라디안 변환 값을 반환한다.
    - math.ceil() : 인자로 전달된 숫자보다 큰 값 중 최소 정수를 반환한다. 
    - math.floor() : 인자로 전달된 숫자보다 작은 값 중 최대 정수를 반환한다.
    - math.pi : 3.14 원주율 값이 정의되어 있다.



### import ~ as ~ 문과 모듈 별칭의 사용

- import 모듈명 as 별칭
  - ex) import math as m은 math 모듈을 m이란 별칭으로 참조할 수 있도록 한다.
- 별칭을 사용하면 가독성도 좋아질 수 있고 좀 더 편리하게 코딩을 할 수 있다.



### from ~ import ~ 문을 이용한 선택적 로딩

- 모듈에서 필요한 함수나 클래스등을 선택적으로 로딩해 사용할 때는 from ~ import ~ 문을 이용한다.

- 예시)

  - from math import radians, ceil, floor, pi 

- 명시적으로 선언해 사용하면, 해당 함수가 어느 모듈에서 로딩되어 사용됐는지 명확히 알 수 있으므로 사용을 권장한다.

- 명시적으로 선언해 사용하면 모듈명을 통해 불러오지 않아도 함수와 값이 직접 로딩된다.

  - 예시

    ``` python
    print("radians(90) = {0}".format(radians(90)))
    print("pi = {0}".format(pi))
    ```



### sys 모듈

- **시스템과 관련된 정보에 접근**하거나 명령행에서 전달된 **명령행 매개변수로부터 인자 값을 읽어올 때 활용**된다.

  ``` python
  import sys
  
  print("sys.argv => {0} {1}".format(type(sys.argv), sys.argv))
  
  for i, val in enumerate(sys.argv): # Enumerate 객체로 변환 및 반복 실시 
      print("sys.argv[{0}] => {1}".format(i, val)) # 인덱스는 변수 i에, 인자 내용은 변수 val에 담겨 출력
  ```

- sys.argv : 리스트 타입, 명령행에서 python 명령에 전달된 인자들의 정보를 담고 있다. 



### random 모듈

- **난수(연속적인 임의의 수)를 생성**하는 기능을 제공한다.

- random 모듈 내 함수들

  - random() 함수 : 0.0 <= N < 1.0 범위의 부동소수점 난수 N을 반환한다.

  - uniform() 함수 : 지정된 범위 내의 부동소수점 난수 N을 반환한다.

    - uniform(1.0, 10.0)

  - randrange() : 정수형 난수 N을 생성한다. start 정보 생략 시 0, steop 정보 생략 시 1 이 기본 값이다. 

  - choice() : 인자로 전달된 시퀀스 객체의 항목 중 임의 항목을 반환한다.

  - choices() : 인자로 전달된 시퀀스 객체의 항목 중 임의의 K개 반환 한다. 복원 추출 기능을 가진 시뮬레이션 함수다. 

    ``` python
    data_list = [1, 2, 3, 4, 5]
    
    print("chocies({0}) => {1}".format(data_list, choices(data_list, k=2)))
    # data_list에서 임의의 값 3을 추출하고 한 번 더 복원하여 출력한다.
    # 출력결과 : chocies([1, 2, 3, 4, 5]) => [3, 3]
    print("sample({0}) => {1}".format(data_list, sample(data_list, k=2)))
    # 출력결과 : chocies([1, 2, 3, 4, 5]) => [3, 2]
    # 출력된 3이 제외되고 나머지 항목에서 추출된다. 
    ```

  - sample() : 인자로 전달된 시퀀스 객체, 혹은 set 객체 항목 중 임의의 k개 반환, 비복원추출 기능을 가진 시뮬레이션 함수
  - shuffle() : 인자로 전달된 시퀀스 객체의 항목을 뒤섞는 함수다. 반환값은 없고 원본 객체의 항목의 순서를 뒤섞는다.



### datetime 모듈

- **날짜와 시간 정보를 확인하고 조작**하는 클래스, 함수 등을 제공한다.

  ``` python
  from datetime import datetime, timezone, timedelta
  
  now = datetime.now() # 현재 지역의 날짜와 시각 정보를 가진 datetime 객체를 얻음
  print(now.year + now.month + now.day + now.hour + now.minute + now.second)
  
  ```

  



## 서드파티 모듈 설치 및 활용

파이썬에서는 표준모듈을 제공하지만 표준모듈이 모든 목적에 부합하는 것은 아니며 모든 기능을 제공하는 것은 아니다.



### 서드파티 모듈

- 다른 누군가에 의해 만들어져 **배포되고 공유**되는 모듈 
- 파이썬의 표준모듈 내용이 부족하거나 없을 때 서드파티 모듈을 사용해 문제를 해결할 수 있다.

### 서드파티 모듈 설치 및 제거 방법

- pip install 모듈명

- pip uninstall 모듈명  



## 사용자 정의 모듈

필요한 기능을 직접 구현한 사용자 정의모듈 만들기

- 파이썬에서 모듈은 파일 단위로 관리된다. 파일명이 곧 모듈명이 된다. 

- 모듈은 **실행**의 목적과 **라이브러리**의 목적을 가진다.

- 모듈은,

  - 파이썬 명령에 의해 실행되는 **실행의 목적**과
  - import 문에 의해 로딩되는 **라이브러리의 목적**으로 나뉠 수 있다.

  ``` python
  import module_mycalc_1
  
  op1, op2 = 2, 3
  result = module_mycalc_1.plus(op1, op2)
  ```

### 모듈의 __name__속성

#### 실행 목적의 모듈

-  실행 목적의 모듈은 __ name __ 속성에 " __ main __ " **문자열 값**이 들어가 있다.

#### 라이브러리 목적의 모듈

- 라이브러리 목적의 모듈은 __ name __ 속성에 **모듈의 이름이 저장**되어 있다.

``` python
#첫번째 라이브러리 모듈을 변경하는 예
def plus(x, y):
    return x + y

def minus(x, y):
    return x - y

if __name__ = "__main__": ##파이썬 명령으로 모듈을 직접 실행
    print("plus(3, 2) => {0}".format(plus(3, 2)))
```







## 사용자 정의 패키지

- 모듈이 모여서 폴더를 구성하면 패키지를 만들 수 있다. 

### 패키지 생성하기

- 패키지를 생성하기 위해서는 먼저 **폴더를 생성**해야 한다.
- 폴더 내에 모듈과 __ init __.py 를 만들어 다음과 같이 작성한다.

``` python
__all__ = ["module_mycalc_1", "module_mycalc_2"] # __all__ 속성에 패키지에 포함될 모듈이름을 저장한다.
```

### 패키지 사용하기

패키지를 사용하는 대표적인 방법은 from ~ import 문이다.

모듈을 선택적으로 로딩하여 사용하는 방법과 동일하게 from 패키지명 import 모듈명 형식으로 사용한다. 

``` python
from package_mycalc import module_mycalc_1 #선택적 모듈 로딩
from package_mycalc import # 모든 모듈을 로딩
```





