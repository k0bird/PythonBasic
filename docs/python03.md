## 3주차_클래스의 사용과 상속

### ◆ 파이썬 클래스 선언 예시

- 파이썬의 클래스 식별자는 카멜케이스(CarmelCase)를 사용

ex) 

```python
class Person:
    # 생성자 메서드 (__init__)
    def __init__(self, name):
        self.name = name  # 인스턴스 변수 초기화

    # 메서드 정의
    def hello(self):
        return f"안녕하세요, 저는 {self.name}입니다."

# 클래스 사용 예시
person1 = Person("박민규")  # Person 클래스의 인스턴스 생성
print(person1.hello())         # "안녕하세요, 저는 박민규입니다."

person2 = Person("김영하")
print(person2.hello())         # "안녕하세요, 저는 김영하입니다."
```
