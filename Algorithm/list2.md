# 배열

list와 배열의 차이점 ... 추가로 찾아보기

Array(배열) : 크기가 고정되어있다. (한번 선언되면 길이가 늘지도, 줄지도 않는다.)

lsit(linked list): 크기를 조절할 수 있다.



 ## 2차원 배열

- 1차원 list를 묶어놓은 list

- 세로길이(행의 개수)와 가로길이(열의 개수)를 필요로 함

  ex)

  2행 4열의 2차원 list

  `arr = [[0, 1, 2, 3], [4, 5, 6, 7]]`



### 배열 순회

: n X m list의 n*m개의 모든 원소를 조사하는 방법

- 행 우선 순회

  ex)

  ```python
  arr = [[0, 1, 2, 3],
  			[4, 5, 6, 7],
  			[8, 9, 10, 11]]
  # i : 행의 좌표, n = len(arr)
  # j : 열의 좌표, m = len(arr[0])
  
  for i in range(len(arr)):
    for j in range(len(arr[i])):
      arr[i][j]
  ```

  

- 열 우선 순회

  ```python
  arr = [[0, 1, 2, 3],
  			[4, 5, 6, 7],
  			[8, 9, 10, 11]]
  # i : 행의 좌표, n = len(arr)
  # j : 열의 좌표, m = len(arr[0])
  
  for j in range(len(arr[0])):
    for i in range(len(arr)):
      arr[i][j]
  ```

  

- 지그재그 순회

  ```python
  arr = [[0, 1, 2, 3],
  			[4, 5, 6, 7],
  			[8, 9, 10, 11]]
  # i : 행의 좌표, n = len(arr)
  # j : 열의 좌표, m = len(arr[0])
  
  for i in range(len(arr)):
    for j in range(len(arr[0])):
      arr[i][j + (m-1-2*j)*(i%2)]
  ```

  

### 델타를 이용한 2차 list 탐색

: 한 좌표에서 4방향의 인접 list 요소를 탐색할 때 사용

- 델타값 = 한 좌표에서 네 방향 좌표와 x, y차이를 저장한 list로 구현

  ```python
  ary[0....n-1][0...n-1]
  dx[] <- [0, 0, -1, 1] # 상하좌우
  dy[] <- [-1, 1, 0, 0]
  
  for x in range(len(ary)):
  	for y in range(len(ary[x])):
  		for I in range(4):
  			testX <- x + dx[mode]
  			testY <- y + dy[mode]
  			test(ary[testX][testY])
  
  ```

  

### 전치 행렬

: 행과 열의 값이 반대인 행렬 ... 잘 쓰진 않는다

```python
arr = [[0, 1, 2],
			[3, 4, 5],
			[6, 7, 8]]
# i : 행의 좌표, n = len(arr)
# j : 열의 좌표, m = len(arr[0])

for i in range(len(3)):
  for j in range(3):
    if i < j:
      arr[i][j], arr[j][i] = arr[j][i], arr[i][j]
```



## 부분집합

- 집합의 원소가 n개일 때 공집합을 포함한 부분집합의 수 = 2n개



### 비트 연산자

: 0과 1로 이루어진 이진수에 대한 연산을 수행하는 연산자 - 2진법 생각

```markdown
& : 비트 단위로 AND 연산
	두 값의 각 자릿수를 비교해 두 값 모두에 1이 있는 경우에만 1을, 나머지는 0을 계산
	3 & 5 = 1
	왜냐면 3을 2진법으로 표현하면 011(2) 이고 5를 2진법으로 표현하면 101(2) 인데
  한자리씩 비교했을 때 2의0승 자리만 맞기 때문에 1 return
| : 비트 단위로 OR 연산
	두 값의 각 자릿수를 비교해 둘 중 하나라도 1이 있으면 1을, 나머지는 0을 계산
	3 | 5 = 7
<< : 피연산자의 비트 열을 왼쪽으로 이동
	2의 몇제곱을 곱해줬냐로 생각할 수 있다.
	2 << 3 : 16 (2 곱하기 2의 3제곱)
	5 << 2 : 20 (5 곱하기 2의 2제곱)
>> : 피연산자의 비트 열을 왼쪽으로 이동
```



## 검색

: 저장되어있는 자료 중 원하는 항목을 찾는 작업



### 순차 검색(sequential search)

: 일렬로 되어 있는 자료를 순서대로 검색

- 첫번째 원소부터 순서대로 비교하며 찾는다.
- 마지막에 이를때까지 검색 대상을 찾지 못하면 검색 실패

**index 검사** 먼저 꼭 해주는 게 중요!

ex)

```python
def sequentialSearch(a, n, key)
	i <- 0
  i <- i+1
  while i<n and a[i]<key:  # while i<n이 index 검사!!
    i <- i+1
  if i<n and a[i] = key:
    return 1
  else:
    return -1
```



### 이진 검색(binary search)

: 자료의 가운데에 있는 항목의 키 값과 비교해 다음 위치를결정하고 검색을 진행

- 자료가 정렬된 상태에서 이진 검색 가능

- 작으면 왼쪽 반에 대해서, 크면 오른쪽 반에 대해 새로 검색

  ```python
  def binarySearch(a, key):
    start = 0
    end = len(a)-1
    while start <= end:
      middle = start + (end-start) // 2
      if key == a[middle]:  # 검색 성공
        return True
      elif key < a[middle]:  # 중간값보다 key가 작을 때
        end = middle - 1
       else:  # 중간값보다 key가 클 때
        start = middle + 1
      return False. # 검색 실패
  ```

  

### 인덱스

- 인덱스는 키-필드만 가지고 있고 테이블의 다른 세부 항목은 가지고 있지 않음



> list를 사용한 인덱스

- 대량 데이터의 성능 저하 문제를 해결하기 위해 사용



## 정렬

### 선택 정렬

: 주어진 자료 중 가장 작은 값의 원소부터 차례대로 선택하여 위치 교환

- 교환 횟수가 버블/삽입 정렬보다 적음



### 셀렉션 알고리즘

: 저장된 자료부터 k번째로 크거나 작은 원소를 찾는 방법

1. 정렬 알고리즘을 이용해 정렬
2. 원하는 순서의 원소 가져오기



