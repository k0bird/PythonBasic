## 3주차_클래스의 사용과 상속

### ◆ 파이썬 클래스 선언 예시

- 파이썬의 클래스 식별자는 카멜케이스(CarmelCase)를 사용

ex1) 

```python
class Person:
    def __init__(self, name):
        self.name = name  # 인스턴스 변수 초기화

    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

person1 = Person("김지훈")  # Person 클래스의 인스턴스 생성
print(person1.hello())         # "안녕하세요, 저는 김지훈입니다."

person2 = Person("홍길동")
print(person2.hello())         # "안녕하세요, 저는 홍길동입니다."
```

ex2)

```python
class Person:
    def __init__(self, name, age=0):
        self.name = name  # 인스턴스 변수 초기화
        self.age = age

    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

    def get_age(self):
        if not self.age:
            return "신생아입니다."
        return f"{self.age}살 입니다."

person1 = Person("홍길동", 36)
print(person1.hello())         # "안녕하세요, 저는 홍길동입니다."

print(person1.get_age())       # 36살 입니다.
```

ex3)

```python
class Person:
    def __init__(self, name, age=0):
        self.name = name  # 인스턴스 변수 초기화
        self.age = age

    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

    def get_age(self):
        if not self.age:
            return "신생아입니다."
        return f"{self.age}살 입니다."

    def gura_chk(self, target):
        target.age += 1
        return f"그의 말은 구라입니다. {target.name}의 나이는 {target.age}살 입니다."

# 클래스 사용 예시
person1 = Person("홍길동", 36)
print(person1.hello())
print(person1.get_age())

person2 = Person("아무개", 27)
print(person2.hello())
print(person1.gura_chk(person1))

print(person1.get_age())

-----------------------------------------------------
안녕하세요, 저는 홍길동입니다.
36살 입니다.
안녕하세요, 저는 아무개입니다.
그의 말은 구라입니다. 홍길동의 나이는 37살 입니다.

37살 입니다.
-----------------------------------------------------
```

### ◆ 클래스의 상속과 오버라이딩


```python
class Person:
    def __init__(self, name):
        self.name = name

    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

class Player(Person):
    def hello(self):
        return f"안녕하세요, 저는 {self.name}(이)라고 하는 플레이어입니다."

class Monster(Person):
    def hello(self):
        return f"반갑다, 나는 {self.name}(이)라고 하는 몬스터이다."


person1 = Player("홍길동")
person2 = Monster("고블린")

print(person1.hello())         # "안녕하세요, 저는 홍길동라고 하는 [플레이어]입니다."
print(person2.hello())         # 반갑다, 나는 고블린(이)라고 하는 몬스터이다.
```

### ◆ 종합 예제 : 간단한 텍스트 기반 RPG 게임 만들기

```python
import random

class Person:
    def __init__(self, name, hp, ad):
        self.name = name
        self.hp = hp
        self.ad = ad

    def attack(self, target):
        damage = random.randint(1, self.ad)
        target.hp -= damage
        print(f"{self.name}(이)가 {target.name}에게 {damage}의 피해를 입혔습니다.")


player = Person("홍길동", 100, 20)
monster = Person("고블린", 50, 10)

print(f"{monster.name}을 마주쳤습니다.")

while True:
    action = input(f"\n행동을 선택하세요 (1: 공격, 2: 도망): ")
    if action == "1":
        player.attack(monster)
        if monster.hp > 0:
            print(f"{monster.name}의 남은 체력은 {monster.hp}입니다.")
        else:
            print(f"{monster.name}을 물리쳤습니다.")
            break
        monster.attack(player)
        if player.hp > 0:
            print(f"{player.name}의 남은 체력은 {player.hp}입니다.")
        else:
            print(f"{monster.name}에게 패배하였습니다.\n게임을 종료합니다.")
            break
    elif action == "2":
        print(f"{monster.name}로 부터 도망쳤습니다. 게임을 종료합니다.")
        break
    else:
        print("올바른 행동을 입력하세요.")
        continue
```
