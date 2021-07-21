# 함수



## 함수 기초

> 함수 : 특정한 기능을 하는 코드의 조각(묶음)
>
> 호출되면 코드를 실행하고 return값을 반환하며 종료

- 구조
  - 이름
  - 매개변수(parameters)
  - 바디(body) - Docstring 및 코드
  - 반환값(return)



> Docstring (Document String) : 함수나 클래스의 설명

- `"""` 이용



> 내장함수 (Built-In Functions)

- 파이썬 인터프리터에는 많은 함수와 형(Type)이 내장되어 있음

- ex)

  `input()` , `range()` , `print()` ... etc.



> 함수의 선언

- `def` 키워드를 이용해 함수 선언
- 들여쓰기를 통해 함수 body를 작성
  - Docstring(`"""`)은 함수 body 앞에 선택적으로 작성 가능
- 동작 후 `return` 을 통해 결과 값을 전달
  - 하나의 객체를 반환



> 함수의 호출 : `함수명()` 으로 호출

- 매개변수가 있는 경우 `함수명(값1, 값2, ...)` 으로 호출

- ex)

  ```python
  def foo() :
    	return True
  
  def func(a, b) :
  		return a + b
  ```

  

## 함수 Output

> 함수의 리턴(return)

- 항상 반환되는 값이 있으며, 어떠한 객체라도 상관 없음

- 오직 하나의 객체만 반환됨

  - 복수의 객체를 return하는 경우 : 하나의 `Tuple` 로 반환

    ```python
    def foo(a, b) :
    		return a+b, a-b
    	
    # foo(1, 2) = (3, -1)
    # type(foo(1, 2)) = tuple
    ```

    

  - 명시된 return값이 없는 경우 : 하나의 `None` 반환

    ```python
    def greeting() :
    		print('hi')
      
    # greeting = hi
    # type(greeting()) = NoneType
    ```

    

> **주의** - Return VS Print

- return : 함수 안에서만 사용되는 **키워드**
- print : 출력을 위해 사용되는 **함수**



## 함수 Input

> 위치 인자(Positional Arguments)

- 함수 호출 시 인자는 위치에 따라 함수 내에 전달됨



> Prarmeter VS Argument

- parameter : 매개변수

  - 함수가 선언될 때 함수에 입력으로 전달된 값을 받는 변수

    ```python
    # 여기서 a, b가 parameter
    def my_func(a, b) :
    		pass
    ```

    

- argument : (전달)인자 / 인수

  - 함수를 호출할 때 함수에 전달하는 입력 값

    ```python
    # 여기서 1, 2가 argument
    my_func(1, 2)
    ```

    

> 기본 인자 값(Default Arguments Values)

- 기본값을 지정하여 함수 호출 시 인자 값을 설정하지 않도록 함



> 키워드 인자(Keyword Arguments)

- 직접 변수의 이름으로 특정 인자 전달

- 키워드 인자 다음에 위치 인자를 사용할 수 없음

  ```python
  def add(x, y) :
  		return x+y
  
  # 여기서 add(x=2, y=5) 가능
  ```



> 가변 인자 리스트(Arbitary Argument List)

- 함수가 임의의 개수 인자로 호출될 수 있도록 지정 (`*args`)

- 인자들은  `Tuple` 로 묶여 처리되며, 매개변수에 `*` 를 붙여 표현

  ```python
  def add(*args) :
  		for arg in args :
  				print(arg)
  		
  # add(2)
  # add(2, 3, 4) 가능
  ```



> 가변 키워드 인자(Arbitary Keword Arguments) 

- 임이의 키워드 인자를 받기 위해 사용 (`**kwargs`)

- 인자들은 `dictionary` 로 묶여 처리되며, 매개변수에 `**` 를 붙여 표현

  ```python
  def family(**kwargs) :
  		for key, value in kwargs :
  				print(key, ":", value)
  		
  # family(father='a', mother='b', sister='c')
  ```



## 함수 Scope

> Scope

- 전역 스코프(global scope) : 코드 어디에서든 참조 가능
- 지역 스코프(local scope) : 함수 내부에서만 참조 가능



> 변수

- 전역 변수(global variable) : 전역 스코프에 정의된 변수
- 지역 변수(local variable) : 지역 스코프에 정의된 변수



> 변수 수명주기(lifecycle)

: 변수는 각자의 lifecycle이 존재

- built-in scope : 영원히 유지
- global scope : 모듈 호출 시점 이후 / 인터프리터가 끝날 때까지 유지
- local scope : 함수 호출 시 생성 / 종료때까지 유지

ex)

```python
def func() :
		a = 20
		print('local', a)
func()
print('global', a)

# local 20은 프린트되지만
# global은 프린트되지 않음 ('a'가 정의되지 않아서)
```



> 이름 검색 규칙(Name Resolution)

- LEGB Rule을 따라 이름을 찾아나감
  - Local scope : 함후
  - Enclosed scope : 특정 함수의 상위 함수
  - Global scope : 함수 밖의 변수, Import 모듈
  - Built-in scope : 파이썬 안에 내장된 함수
- 함수 내에서는 바깥 스코프의 변수에 접근이 가능하나 수정은 할 수 없음



> global

- 현재 코드 블록 전체에 적용되며 나열된 식별자들이 전역변수임을 나타냄

- local scope에서 global 변수 값을 변경 가능  # 별로 좋은 코드는 아니다..

  (global 키워드를 사용하지 않으면 local scope에 a 변수가 생성)

  ex)

  ```python
  a = 10
  def func() :
  		global a
  		a = 3
  	
  print(a) # a = 10
  func(a)
  print(a) # a = 3
  ```



> nonlocal

- 전역을 제외, 가장 가까운(상위의) 스코프의 변수를 연결

- global과 달리 이미 존재하는 이름과의 연결만 가능

  (global은 선언된 적 없는 변수에도 할당 가능 / nonlocal은 선언된 적 없는 변수에는 할당 불가)







## 재귀함수

> 재귀함수(Recursive Function)

- 자기 자신을 호출하는 함수
- 알고리즘 설계 및 구현에 유용하게 활용
- 무한정 호출을 방지하기 위해 1개 이상의 base case(종료되는 상황)가 존재, 수렴하도록 작성



> 팩토리얼

```python
# 반복문 Factorial
# 마지막 n이 1이면 stop
def fact(n) :
    result = 1
    while n > 1 :
        result *= n
        n -= 1
    return result
```



```python
# 재귀 Factorial
# 마지막 n이 1이면 stop (base case)
def factorial(n) :
    if n == 1 :
        return n
    else :
        return n * factorial(n-1)
```



> 피보나치

```python
# 반복문
def fibo_for(n) :
    if n < 2 :
        return n
    
    a, b = 0, 1 # a가 0번째 항의 값, 0 / b가 1번째 항의 값, 1
    
    for i in range(n-1) :
        a, b = b, a+b
    return b
```



```python
# 재귀
def fibo(n) :
    # base case
    if n < 2 :
        return n
    else :
        return fibo(n-1) + fibo(n-2)
```



## 에러 / 예외

> 디버깅

- print문 활용
- text editor, IDE 등에서 제공하는 기능 활욜



> 문법 에러(Syntax Error)

- 에러가 감지된 가장 앞의 위치를 가리키는 캐럿 기호(`^`) 표시



> 예외(Exception)

- 실행 도중 예상치 못한 상황을 맞이하면 프로그램 실행을 멈춤

- 문법적으로는 틀리지 않으나 실행 중 감지되는 에러

  

  정리)

  	- ZeroDivisionError : 0으로 나눌 때 발생
  	- NameError : namespace 상 이름이 없는 경우
  	- TypeError : Type 불일치 / argument 누락, 개수 초과, type 불일치
  	- ValueError : type은 올바르나 값이 적절하지않거나 없는 경우
  	- IndexError : 인덱스가 존재하지 않거나 범위를 벗어난 경우
  	- KeyError : 해당 키가 존재하지 않는 경우
  	- ModuleNotFoundError : 존재하지 않는 모듈을 import하는 경우
  	- ImportError : Module은 있지만 존재하지 않는 함수를 가져오는 경우



## 예외 처리

> 예외 처리

- try문 / except 절 이용, 예외처리 가능

- except Exception이 가장 큰 범주로, 예외처리는 가장 작은 범주부터 예외처리해야 함(순차적 수행)

  - try 아래 코드 블록이 실행됨

    - 예외 발생하지 않으면 except절 없이 종료
    - 예외 발생 시 except절 실행

    ex)

```python
try :
    num = input('숫자입력 :')
    print(int(num))
except ValueError : # ValueError에만 반응하는 except문
    print('숫자가 입력되지 않았습니다.')
except : # 그 외에 발생하는 에러에 대한 except문
    print('뭔지 모를 에러가 발생했습니다.')
```



> 정리

- try
  - 코드 실행
- except
  - try문에서 예외 발생 시 실행
- else
  - try문에서 예외가 발생하지 않으면 실행
- finally
  - 예외 발생 여부 관계 없이 항상 실행



## 예외 발생시키기

> raise statement

- `raise` 를 통해 예외를 강제로 발생
- `raise <표현식>(메시지)` 
  - `<표현식>` 에 예외 타입 지정



> assert statement

- `assert` 를 통해 예외를 강제로 발생
- 일반적으로 디버깅 용도로 사용
- 무조건 AssertionError 발생

- `assert <표현식>, <메시지>` 
  - `<표현싯>` 이 False인 경우 AssertionError 발생



## Try문 VS If문

> 기본적으로 Python에서는 try문을 권장하는 성향이 있다.

- try : 예외처리를 활용해 검사를 수행하지 않고 일단 실행하고 예외처리를 진행

  (허락보다 용서가 쉽다...!)

- if : 실행하기 전 에러가 날만한 요소들을 조건문으로 검사하고 실행

