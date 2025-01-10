## 3주차_클래스의 사용과 상속

### ◆ 파이썬 클래스 선언 예시

- 파이썬의 클래스 식별자는 카멜케이스(CarmelCase)를 사용

ex1) 

```python
class Person:
    # 생성자 메서드 (__init__)
    def __init__(self, name):
        self.name = name  # 인스턴스 변수 초기화

    # 메서드 정의
    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

# 클래스 사용 예시
person1 = Person("김지훈")  # Person 클래스의 인스턴스 생성
print(person1.hello())         # "안녕하세요, 저는 김지훈입니다."

person2 = Person("홍길동")
print(person2.hello())         # "안녕하세요, 저는 홍길동입니다."
```

ex2)

```python
class Person:
    # 생성자 메서드 (__init__)
    def __init__(self, name, age=0):
        self.name = name  # 인스턴스 변수 초기화
        self.age = age

    # 메서드 정의
    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

    def get_age(self):
        if not self.age:
            return "신생아입니다."
        return f"{self.age}살 입니다."

# 클래스 사용 예시
person2 = Person("홍길동", 36)
print(person2.hello())         # "안녕하세요, 저는 홍길동입니다."

print(person2.get_age())       # 36살 입니다.
```

### ◆ 클래스의 상속과 오버라이딩

ex3)

```python
class Person:
    def __init__(self, name, age=0):
        self.name = name
        self.age = age

    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

    def get_age(self):
        if not self.age:
            return "신생아입니다."
        return f"{self.age}살 입니다."

class Player(Person):
    def hello(self):
        return f"안녕하세요, 저는 {self.name}라고 하는 사람입니다."



person2 = Player("홍길동", 36)
print(person2.hello())         # "안녕하세요, 저는 홍길동라고 하는 [사람]입니다."
```
