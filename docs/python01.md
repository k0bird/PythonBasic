## 1주차_파이썬 언어의 이해, 기본 개념

### ◆ 파이썬이란?
[파이썬_나무위키](https://namu.wiki/w/Python)

### ◆ 파이썬 설치
[https://www.python.org/](https://www.python.org/)

### ◆ 커맨드라인(cmd), 내장에디터 활용 입출력
- print(): 화면에 출력하는 함수
- input(): 사용자로부터 입력을 받는 함수
  
```python
print("Hello World!")
    
print(input("출력 할 문자를 입력하세요: "))
```

### ◆ 변수와 자료형(Type)
- 파이썬에서는 변수를 선언할 때 자료형을 지정하지 않아도 됨
- 변수에 값을 대입하면 자동으로 자료형이 결정됨
- type(): 변수의 자료형을 확인하는 함수

```python
a = 32
b = 32.3
c = float(32)
d = "32.3"

print(type(a))
print(type(b))
print(type(c))
print(type(d))
```

### ◆ 사칙연산
- /: 나누기(소수점까지 계산)
- //: 몫
- %: 나머지

### ◆ 배열(list)
- 리스트는 여러 값을 저장할 수 있는 자료구조
- 리스트는 [] 또는 list()로 생성 가능
- 값을 추가하려면 .append, 제거하려면 .remove를 사용

```python
ex_list = list() ### or ex_list = []
ex_list.append(1)
ex_list.append(2)
ex_list.append(3)
ex_list.append(4)
ex_list.remove(3)

print(ex_list)
```

### ◆ 조건문(if)

- 파이썬의 조건문은 소괄호를 사용하지 않고, 중괄호 대신 들여쓰기로 블록을 구분함.

```python
number = int(input("숫자를 입력하세요: "))
if number > 10:
    print("10보다 큽니다")
else:
    print("10보다 크지 않습니다")

```

### ◆ 조건문(while, for)
- while: 조건이 참일 때 까지 반복
```python
i = 1
while i <= 10:
    print(i)
    i += 1
```

- for: 특정 횟수나 순회 가능한 객체의 항목을 반복
```python
numbers = [1, 2, 3, 4, 5]
for number in numbers:
    print(number)
```

### ◆ 종합 예제
- 사용자로부터 두 개의 숫자를 입력받아, 두 숫자의 합, 차, 곱, 몫, 나머지를 각각 출력하세요.
```python
  # 두 개의 숫자 입력받기
  num1 = float(input("첫 번째 숫자를 입력하세요: "))
  num2 = float(input("두 번째 숫자를 입력하세요: "))
  
  # 계산 수행
  addition = num1 + num2
  subtraction = num1 - num2
  multiplication = num1 * num2
  
  # 나눗셈과 나머지 계산 (두 번째 숫자가 0인 경우 예외 처리)
  if num2 != 0:
    division = num1 / num2
    remainder = num1 % num2
  else:
    division = "나눗셈 불가 (0으로 나눌 수 없음)"
    remainder = "나머지 계산 불가 (0으로 나눌 수 없음)"
  
  # 결과 출력
  print(f"두 숫자의 합: {addition}")
  print(f"두 숫자의 차: {subtraction}")
  print(f"두 숫자의 곱: {multiplication}")
  print(f"두 숫자의 몫: {division}")
  print(f"두 숫자의 나머지: {remainder}")
```

- 리스트에 문자열 "apple", "banana", "cherry"를 추가한 후, for 문을 사용하여 각 항목을 출력하세요.
```python
  # 리스트 생성 및 문자열 추가
  fruits = ["apple", "banana", "cherry"]
  
  # for 문을 사용하여 각 항목 출력
  for fruit in fruits:
      print(fruit)
```

- while문을 사용하여 1부터 100까지의 짝수를 모두 출력하세요.
```python
  # 초기값 설정
  number = 1
  
  # while문으로 1부터 100까지 순회
  while number <= 100:
      if number % 2 == 0:  # 짝수인지 확인
          print(number)
      number += 1
```

