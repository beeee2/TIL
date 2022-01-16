오류는 **해석 단계**에서 발생하는 **구문 오류**와 **실행 단계**에서 발생하는 **예외(exception)**로 구분된다.

오류를 빠르게 해결하기 위해서는 오류 발생시 나타나는 오류 메세지를 확인해봐야 한다. 



## 구문 오류와 예외

### 구문오류

**잘못된 명령을 입력**해 발생하는 오류다.

오타나 문법적으로 필수적인 요소가 빠지진 않았는지 찾아 재코딩해야 한다.



### 예외

문법적인 문제는 없는데 **실행 중에 예기치 않게** 발생한 오류다.



## 예외 처리 방법

1. if 문을 이용한 예외의 처리
   - 정상적인 흐름을 제어할 경우에만 사용 가능하다.
   - 예외 발생 상황을 사전에 제어하는 코드에 가깝다. 
2. try ~ except 문을 이용한 예외의 처리
   - 예외가 발생했을 때 처리
3. try ~ except ~ else 문을 이용한 예외의 처리
   - 예외가 발생했을 때 처리, 예외가 발생하지 않았을 때를 나누어 처리한다.
4.  try ~ except ~ else ~ finally 문을 이용한 예외의 처리 
   - 예외가 발생했을 때 처리, 예외가 발생하지 않았을 때, 예외 발생과 상관없이 실행되는 코드를 나누어 작성할 수 있다.





## 예외 객체

코드를 실행 중 오류가 발생하면 만들어진 것으로, **오류 발생과 관련한 정보**를 가지고 있다. 

다중 except 문을 이용하여 예외 객체에 따른 처리의 분기가 가능하다.



## 강제로 예외를 발생시키는 방법

특정 조건에서 예외 객체를 만들어 예외를 일으킬 수 있다. 

### raise 문을 이용한 강제 예외 발생

``` python
def calc_area(w, h):
    if w.isdigit() and h.isdigit():
        return int(w) * int(h)
    else:
        raise ValueError("숫자가 아닌 값이 입력되었습니다.")
        
print("사각형의 면적을 구해봅시다.")

width = input("폭을 입력하세요 : ")
height = input("높이를 입력하세요 :")

try:
    area = calc_area(width, height)
except ValueError as ve:
    print("{0}: {1}".format(type(ve), ve))
except Exception as ex:
    print("{0}: {1}".format(type(ex), ex))
else:
    print("{0} x {1} = {2}".format(width, height, area))
finally:
    print("finally 코드 블록은 예외 발생 여부에 상관없이 실행됩니다.")
    
print("프로그램을 종료합니다...")
```





























