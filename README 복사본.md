# 구현과정 상세 설명

## 1단계

### 풀이법
- 입력값
  - 파이썬에서 줄바꿈(\n)을 포함한 문자열은 '''로 표현할 수 있다.
  
- 2차원배열로 저장하기
  
  convert_num함수 : 기호들을 숫자로 바꾸어준다.
  
  ```python
  dimensional_array = [i for i in re.sub('[#OoP=]', convert_num, s).split('\n')]
  ```
  
  - 입력 받은 문자열에서 기호에 따라 숫자를 바꾸어주고, 2차원배열을 만들기 위해 `줄바꿈('\n')`기준으로 나누어준다.




- 출력하기

  ```python
  for i in re.split('\n=.+\n', s):
      print(i) # stage별로 출력
      a = re.split('\n', i)
      # ['Stage 1', '#####', '#OoP#', '#####']
      print("가로크기", len(max(a[1:], key=lambda x: len(x))))
      print("세로크기", len(a[1:]))
      print("구멍의 수", i.count('O'))
      print("공의 수", i.count('o'))
      for index, k in enumerate(a):
          if 'P' in k:
              print("({}, {})".format(index,k.index('P')+1))
  ```

  1 . Stage 별로 나누기

     `re.split('\n=.+\n', s)`

     입력받은 값을 `====` 기준으로 나누어준다.

     - 출력값

     ```
     Stage 1
     #####
     #OoP#
     #####
     ```
  
  2 . 줄바꿈기준으로 나누어준다.
  
     `a = re.split('\n', i)`
  
     - 출력값
  
     `['Stage 1', '#####', '#OoP#', '#####'] `
  
  3 .  `Stage X`를 제외하고 남은 배열 = `a[1:]`= `['#####', '#OoP#', '#####']`에서 가로, 세로크기를 구한다.
  
  4 . 구멍/공의 수 구하기
    ```python
    print("구멍의 수", i.count('O'))
    print("공의 수", i.count('o'))
    ```
    여기서 i 는
    ```
     Stage 1
     #####
     #OoP#
     #####
    ```
    이다. 여기서 구멍과 공을 카운트한다.
  
  5 . 플레이어의 위치를 찾는다.
    ```python
    for index, k in enumerate(a):
    	if 'P' in k:
      	print("플레이어의 위치 : ({}, {})".format(index, k.index('P')+1))
    ```
    여기서 a 는
	
    `['Stage 1', '#####', '#OoP#', '#####'] ` 이다.


## 2단계

## 3단계