## 4주차_장고(Django)프레임워크를 이용한 웹개발


### ◆ 장고(Django)란 ?

![image](https://github.com/user-attachments/assets/07b73fea-e168-4f9c-9963-f2c0ba3cdd75)

The web framework for perfectionists with deadlines = 마감일에 쫓기는 완벽주의자를 위한 웹 프레임워크

개발 속도가 빠르고, 보안이 훌륭하고, 기능이 많다.


### ◆ 장고의 디자인 패턴(MTV)

- MTV(Model Template View)

- Model

```
데이터베이스(DB)에 저장되는 데이터에 대한 관리, 연결, 실행의 역할
SQL을 사용하지 않고 DB작업을 가능하게 하는 ORM(Object-Relational Mapping)을 제공한다.
ORM : 입문자에게 더 쉽고 탄탄함
(models.py)
```

- View

```
컨트롤러의 역할.
웹 요청을 받으면 로직에 따라 필요한 데이터를 Model을 통해 추출, 가공하여 템플릿으로 보내준다.
(veiws.py)
```

- Template

```
사용자에게 보이는 부분을 관리.
View로부터 전달받은 데이터 등을 가시화 하여 사용자에게 보여준다.
(.html)
```


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

### ◆ 어플리케이션(App) 만들기

```
djnago-admin startapp myapp
```

- 새로 생성한 앱 추가

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',  # 새로 생성한 앱 추가
]
```

### ◆ URL 연결

- config > urls.py
  
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
```


- myapp > urls.py (생성)

```python
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index),
]
```


### ◆ 간단한 뷰(views) 출력 사용해보기

- myapp > views.py

```python
from django.http import HttpResponse


def index(request):
    return HttpResponse("안녕하세요 myapp에 오신것을 환영합니다.")
```


