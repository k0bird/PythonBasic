## 2주차_함수와 라이브러리 활용

### ◆ 파이참(IDE) 설치하기
[파이참 다운로드](https://www.jetbrains.com/pycharm/download/?section=windows)


### ◆ 파이썬 식별자(변수명, 함수명) 선언규칙
- 특수문자는 언더 바(_)만 사용
- 숫자로 시작 x
- 공백 x
- 기본 키워드를 피해서
- 되도록 유의미하고 의도를 알 수 있도록 명명


### ◆ 카멜 케이스와 스네이크 케이스
- CamelCaseExample
- snake_case_example

### ◆ 함수 활용(def)
- 예제 1)
  
```python
def func_text():
  return "함수의 반환값입니다."

result = func_text()
print(result)
```

- 예제 2)
  
```python
def input_content():
    content = input("출력 할 내용을 입력하세요: ")
    return content

content = input_content()
print(content)
```

- 예제 3)
  
```python
def input_content():
    text = input("출력 할 내용을 입력하세요: ")
    return text


def get_type(content):
    type_content = type(content)
    return type_content


content = input_content()
type_content = get_type(content)
print(content)
print(type_content)
```


### ◆ 내장 라이브러리를 활용한 난수 생성

```python
import random

ran_int = random.randint(1, 100) 
print(ran_int)
```

- 랜덤 함수를 이용한 업다운게임

```python
import random

ran_int = random.randint(1, 100)  #랜덤 정수가 생성됨
how_many = 0 #시도한 횟수 초기값

print("1부터 100 사이의 숫자를 맞춰보세요!")

while True:
    input_num = int(input("숫자를 입력하세요: "))
    how_many += 1 #시도 횟수 증가

    if input_num < ran_int:
        print("UP!")
    elif input_num > ran_int:
        print("DOWN!")
    else:
        print(f"정답입니다! {how_many}번 만에 맞추었습니다.")
        break
```

### ◆ 사전(dictionary) 자료형

```python
ex_dict = {} # ex_dict = dict()
ex_dict[1] = "더하기"
ex_dict[2] = "빼기"
ex_dict["생선"] = 3000
ex_dict["물고기"] = ["광어", "우럭"]

print(ex_dict)

{1: '더하기', 2: '빼기', '생선': 3000, '물고기': ['광어', '우럭']}
```

### ◆ 실습예제 : 계산기 만들기

```python
def op_exec(op_num, num1, num2):
    calc = 0
    if op_num == 1:                         # 더하기
        calc = num1 + num2
    elif op_num == 2:                       # 빼기
        calc = num1 - num2
    elif op_num == 3:                       # 곱하기
        calc = num1 * num2
    elif op_num == 4:                       # 나누기
        if num2 == 0:
            return "0으로 나눌 수 없습니다."
        calc = num1 / num2
    return calc


op_dict = {}
op_dict[1] = "더하기"
op_dict[2] = "빼기"
op_dict[3] = "곱하기"
op_dict[4] = "나누기"

while True:
    print("1. 더하기")
    print("2. 빼기")
    print("3. 곱하기")
    print("4. 나누기")
    print("5. 종료")

    op_num = int(input("실행 할 동작을 입력하세요. (1/2/3/4/5): "))
    if op_num not in [1, 2, 3, 4, 5]:       # 입력한 옵션이 1~5 가 아닐 경우
        print("올바른 명령을 입력하세요.")
        continue
    if op_num == 5:                         # 5일 경우 계산기 종료
        print("계산기가 종료 되었습니다.")
        break

    op_text = op_dict[op_num]  # 옵션 이름 가져오기
    print(f"{op_text} 를 선택 하셨습니다.")

    try:                                # 시도
        num1 = float(input("첫번째 숫자: "))
        num2 = float(input("두번쨰 숫자: "))
    except ValueError:                  # 값 에러 시(실수가 아닐 시)
        print("숫자를 입력하세요")
        continue                        # 중지 후 다시 반복


    calc_result = op_exec(op_num, num1, num2)   # 계산값 가져오기

    print(f"실행결과: {calc_result}\n")     # \n 줄바꿈



########################################################
1. 더하기
2. 빼기
3. 곱하기
4. 나누기
5. 종료
실행 할 동작을 입력하세요. (1/2/3/4/5): 1
더하기 를 선택 하셨습니다.
첫번째 숫자: 3
두번쨰 숫자: 5
실행결과: 8.0

1. 더하기
2. 빼기
3. 곱하기
4. 나누기
5. 종료
실행 할 동작을 입력하세요. (1/2/3/4/5): 
```




