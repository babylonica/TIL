# 파이썬 기초



## 기초 문법

> 코드 스타일 가이드

- PEP 8 (Python Style Guide)
- Google Style Guide



> 주석

- `#` : 블럭 잡아서 `control+/`

- docstring : 함수 / 클래스의 설명서 

  ```python
  ​```
  ...
  ​```
  ```



## 변수와 식별자

> 변수 : 할당연산자(=)를 통해 값을 할당 (assign)

- `type()` : 변수에 할당된 값의 타입 확인
- `id()` : 객체의 메모리 주소를 확인



> 식별자 : 변수, 함수, 크래스 등을 식별하는데 사용하는 이름

- 영문 알파벳, 언더바(_), 숫자로 구성



## 데이터 타입

> 숫자(Number)

- int(정수) : 모든 정수는 int type
- float(실수)
- complex(복소수)
  - 허수부를 'j'로 표현
  - a.real : 실수부, a.imag : 허수부



> 문자열(String)

- escape sequence : 문자열 내 특정 문자나 조작을 위해 역슬래시`\`를 활용, 구분


- String Interpolation : 변수의 값을 문자열의 자리 표시자(placeholder)로 대체
  - %-formattiong
  - str.format()
  - **f-string**



> 참/거짓(Boolean)

- True/False 값을 가진 타입은 Bool
- True = 1, False = 0
- 0, (), {}, [], '', None => False로 변환



> None

- 값이 없음을 표현하기 위한 Type



## 타입 변환

> 자료형 변환/타입 변환

- 암시적 : 파이썬 내부적으로 타입 변환
- 명시적 : 사용자가 특정 함수 활용, 의도적으로 타입 변환



## 연산자

> 산술 연산자

- 나눗셈은 항상 결과가 float
- `divmod()` : 몫과 나머지를 한번에 받을 수 있음(내장함수)



> 비교 연산자

- True / False값을 리턴

- is None : 값이 비어있음을 확인할 때



> 논리 연산자

- True / False값을 리턴
- 일반적으로 비교연산자와 함께 사용됨

- **단축평가** : 결과가 확실한 경우 두번째 값은 확인하지 않고 첫번째 값 반환



> 복합 연산자

- 연산과 대입이 함께 이루어짐



> 기타 연산자

- Concatenation : `+` 는 숫자가 아닌 자료형에서도 사용 가능

- Containment Test : 특정 요소가 속해있는지 확인
- Identy : is 연산자를 통해 동일 객체인지 확인
  - -5~256까지 숫자의 id는 동일
- Indexing / Slicing
  - `[]` 를 통해 접근하고 , `[:]` 를 통해 슬라이싱




## 표현식 / 문장

> 식, 표현식 : 하나의 값으로 환원될 수 있는 문장

- 식별자, 값, 연산자로 구성



> 문, 문장 : 파이썬이 실행 가능한 최소한의 코드 단위

- 모든 표현식은 문장



## 컨테이너

> 컨테이너 : 여러개의 값을 저장할 수 있는 것(객체)



### 컨테이너 분류_1

- 시퀀스형 : 순서가 있는(ordered) 데이터
  - (그렇다고 정렬되어있다는건 아님..!)
  - list, tuple, range, string, binary
- 비시퀀스형 : 순서가 없는(unordered) 데이터
  - set, dictionary



### 시퀀스형 컨테이너

> 리스트(list)

- 순서가 있는 시퀀스로 인덱스를 통해 접근

- `[]` 혹은  `list()` 를 통해 생성
- 값 변경 가능



> 튜플

- 수정불가능한(immutable) 시퀀스로 인덱스를 통해 접근
- `()` 혹은 `tuple()` 을 통해 생성
- 값 변경 불가능 => 일반적으로 파이썬 내부에서 활용됨

- 하나의 항목으로 구성된 튜플은 생성시 값 뒤에 쉼표가 붙어야 함



> 레인지

- 숫자의 시퀀스를 나타내기 위해 사용
- 기본형 : 0 ~ n-1까지
  - `range(n)`
- 범위 지정 : n~ m-1
  -  `range(n, m)`
- 범위 및 스텝 지정 : n ~ m-1까지 s만큼 증가하며
  - `range(n, m, s)`





### 비시퀀스형 컨테이너

> 세트

- 순서가 없는 자료구조

- `set()` 을 통해 생성

- 수학에서 '집합'과 동일한 구조를 가짐

  - 차집합 : `-`
  - 합집합 : `|`
  - 교집합 : `&` 

- 중복된 값이 존재하지 않음

  - 중복된 값을 쉽게 제거할 수 있지만 

    순서가 중요한 경우 사용할 수 없음..!



> 딕셔너리

- key와 value가 쌍으로 이루어진 자료구조
  - key를 통해 value에 접근
  - key : 변경 불가능한 데이터만 활용 가능
  - value는 모든 값으로 설정 가능
- `{}` 혹은 `dict()` 을 통해 생성

 



### 컨테이너 분류_2 Mutable VS Immutable

- 변경 불가능한(immutable) 데이터 : 재할당
  - 숫자, 문자열, 참/거짓
  - range, tuple
- 변경 가능한(mutable) 데이터 : 동일한 객체의 주소를 참조
  - list
  - set
  - dictionary




## 제어문

> 조건문

- if문은 참/거짓을 판단할 수 있는 조건식과 함께 사용

- if, else

> 복수 조건문

- if, elif, else
- 조건식을 동시에 비교하는 것이 아니라 순차적으로 비교..!



## 반복문

>  while문 : 종료 조건에 해당하는 코드를 통해 종료 필요

- 조건식이 참인 경우 반복적으로 코드 실행

- 무한 루프를 하지 않도록 종료조건이 반드시 필요

  

> for문 : 반복 가능(iterable)한 객체를 순회하면 종료

- 별도의 종료조건 불필요

- Enumerate

  : `(index, value)` 형태의 Tuple로 구성된 객체 반환

  ex)

  ```python
  fruits = ['apple', 'banana', 'grape']
  
  for idx, fruit in enumerate(fruits) :
  	print(idx, fruit)
  ```

  0 apple

  1 banana

  2 grape

> 반복 제어 : break, continue, for-else

- break

  - 반복문 종료

- **continue**

  - continue 이후 코드 블록은 수행하지 않고

    다음 반복을 수행

- for-else

  - 끝까지 반복문 실행 후 else문 수행
  - break를 통해 중간에 종료되는 경우 else문은 실행되지 않음
  
  

> pass

- 아무것도 하지 않음
- 특별히 할 일이 없을 때 자리를 채우는 용도로 사용
- 반복문이 아니어도 사용 가능

