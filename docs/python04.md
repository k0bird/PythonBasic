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




### ◆ 실습 예제 : TO-DO 웹서비스 만들기

- myapp > models.py 에 To-do 모델을 정의

```python
from django.db import models

class Todo(models.Model):
    title = models.CharField(max_length=200)
    completed = models.BooleanField(default=False)

    def __str__(self):
        return self.title
```

- 데이터베이스에 반영(마이그레이션)

```
python manage.py makemigrations
python manage.py migrate
```

- HeidiSQL(db 브라우저) 설치

https://www.heidisql.com/download.php


- 뷰 작성

```python
from django.shortcuts import render, redirect
from .models import Todo

def todo_list(request):
    todos = Todo.objects.all()
    return render(request, 'todo/todo_list.html', {'todos': todos})

def add_todo(request):
    if request.method == 'POST':
        title = request.POST['title']
        Todo.objects.create(title=title)
        return redirect('todo_list')
    return render(request, 'todo/add_todo.html')

def toggle_todo(request, todo_id):
    todo = Todo.objects.get(id=todo_id)
    todo.completed = not todo.completed
    todo.save()
    return redirect('todo_list')
```

- URL 설정

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.todo_list, name='todo_list'),
    path('add/', views.add_todo, name='add_todo'),
    path('toggle/<int:todo_id>/', views.toggle_todo, name='toggle_todo'),
]
```

- templates 폴더 생성 및 연결

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

- TO-DO 리스트 템플릿 작성
  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>To-Do List</title>
</head>
<body>
    <h1>To-Do List</h1>
    <a href="/add/">Add To-Do</a>
    <ul>
        {% for todo in todos %}
            <li>
                <form action="/toggle/{{ todo.id }}/" method="post" style="display: inline;">
                    {% csrf_token %}
                    <button type="submit">{{ todo.title }}</button>
                </form>
                {% if todo.completed %} (Done) {% endif %}
            </li>
        {% endfor %}
    </ul>
</body>
</html>
```

- TO-DO 추가 템플릿 작성

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Add To-Do</title>
</head>
<body>
    <h1>Add To-Do</h1>
    <form method="post">
        {% csrf_token %}
        <input type="text" name="title" placeholder="To-Do Title">
        <button type="submit">Add</button>
    </form>
    <a href="/">Back</a>
</body>
</html>
```


