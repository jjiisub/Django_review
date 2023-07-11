# Django 교안

## 1. Django란?

## 2. 환경 세팅

### 1. 프로젝트를 생성하고자 하는 위치에 가상환경 생성

```shell
mkdir FolderName  # 폴더 생성
cd FolderName  # 폴더 directory로 이동
python -m venv MyVenv  # MyVenv라는 이름으로 virtual environment 생성
```

### 2. 생성한 가상환경 활성화

```shell
source venv/bin/activate  # MacOS 기준 -> 윈도우는 명령어가 다름
```

![venv_active](/assets/img/2_venv_activate.png)

```shell
deactivate  # venv 비활성화
```

### 3. 가상환경에 Django 설치

```shell
python -m pip install django
```

- 만약 아래와 같은 경고 문구가 나왔다면 가상 환경 내 django의 경로를 설정한다.
  ![django_install_error](/assets/img/2_django_install_error.png)

  ```shell
  vi .bash_profile  # .bash_profile 파일 생성 후 vim 열기
  ```

  i 를 입력하여 insert 모드를 활성화한 후 아래의 경로를 붙여 넣고 :wq 를 입력하여 저장 후 vim을 빠져나온다. 이때 "Versions/**/bin"에서 ** 위치에는 자신의 환경에 설치된 python version을 넣는다.

  ```
  PATH="/Library/Frameworks/Python.framework/Versions/3.11/bin:${PATH}"
  ```

  vim을 빠져나온 후 아래의 명령어를 실행하여 수정된 경로를 적용한다.

  ```shell
  source .bash_profile
  django-admin  # django-admin 정상 실행 여부를 확인
  ```

## 3. Django Tutorial

---

### 1. Django 프로젝트 생성

```shell
django-admin startproject app . # 현재 위치에 app이라는 이름의 프로젝트 생성
```

정상적으로 프로젝트가 실행된 경우 app 폴더의 구조는 다음과 같다.

```shell
myapp
  ├── app
  │    ├── __init__.py
  │    ├── asgi.py
  │    ├── settings.py
  │    ├── urls.py
  │    └── wsgi.py
  ├── managy.py
  └── venv/
```

```shell
python manage.py migrate  # Django Project 초기 설정 적용
```

---

### 2. 프로젝트 실행

```shell
python manage.py runserver
```

정상적으로 프로젝트가 실행될 경우, CLI 상에 아래와 같은 결과가 나타난다.
![runserver](/assets/img/2-2_runserver.png)
현재 해당 주소의 초기 화면은 다음과 같다.
![runserver_page](/assets/img/2-2_runserver_page.png)

'Control 키 + C' 를 통해 runserver 명령을 중지시킬 수 있다.

---

### 3. 프로젝트 내 앱 생성 & settings.py 수정

```shell
python manage.py startapp blog  # blog 라는 이름의 App을 현재 프로젝트에 생성
```

프로젝트에 앱을 생성하는 경우에는 반드시 myapp/app/settings.py 파일을 수정해야 한다.

```python
## myapp/app/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',  # 새로운 app 추가 시 반드시 목록에 추가해야 함
]
```

### 4. settings.py 초기 설정

위에서 runserver 시 초기 페이지를 보면 영어로 나오는 것을 확인할 수 있다. 프로젝트의 기본 언어를 한국어로 변경하기 위해서는 settings.py를 수정해야 한다.

```python

# LANGUAGE_CODE = 'en-us'
LANGUAGE_CODE = 'ko-kr'

# TIME_ZONE = 'UTC'
TIME_ZONE = 'Asia/Seoul'
```
