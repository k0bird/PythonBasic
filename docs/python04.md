## 4주차_장고(Django)프레임워크를 이용한 웹개발


### ◆ 장고(Django)란 ?

![image](https://github.com/user-attachments/assets/07b73fea-e168-4f9c-9963-f2c0ba3cdd75)

The web framework for perfectionists with deadlines = 마감일에 쫓기는 완벽주의자를 위한 웹 프레임워크

개발 속도가 빠르고, 보안이 훌륭하고, 기능이 많다.


### ◆ 장고 개발 환경 준비(가상 환경)

1. 새로운 프로젝트 생성

2. 가상 환경 생성
   
```
C:\프로젝트 경로> python -m venv myvenv(가상환경이름)
```

3. 가상 환경 활성화

```
C:\프로젝트 경로> venv\scripts\activate
(myvenv) C:\프로젝트경로>
```

4. 가상 환경 비활성화

```
(myvenv) C:\프로젝트경로> deactivate  
c:\프로젝트경로>
```


### ◆ 장고 설치(pip 사용)

1. 가상환경 pip 확인
   
```
pip list
```

2. pip 최신 버전으로 업그레이드
   
```
python -m pip install --upgrade pip
```

3. 장고 설치
   
```
pip install django
```


### ◆ 장고 프로젝트 생성 및 구동

1. 현재 프로젝트경로에 "config"라는 기본프로젝트폴더 생성
   
```
django-admin startproject config .
```

2. 개발 서버 구동

```
python manage.py runserver
```

3. 웹사이트 구동 확인 및 종료
   
```
Starting development server at http://127.0.0.1:8000/ 
Quit the server with CONTROL-C.
```

![image](https://github.com/user-attachments/assets/276dabe0-5428-4c7a-af59-d1e6ed7a4000)

- 서버 언어와 시간 설정

```python
LANGUAGE_CODE = 'ko-kr'

TIME_ZONE = 'Asia/Seoul'
```

### ◆ 장고의 디자인 패턴(MTV)

- MTV(Model Template View)



