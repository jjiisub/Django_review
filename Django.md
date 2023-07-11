# Django 교안

## 1. Django란?

## 2. 환경 세팅

1. 프로젝트를 생성하고자 하는 위치에 가상환경 생성

```shell
mkdir FolderName  # 폴더 생성
cd FolderName  # 폴더 directory로 이동
python -m venv MyVenv  # MyVenv라는 이름으로 virtual environment 생성
```

2. 생성한 가상환경 활성화

```shell
source venv/bin/activate  # MacOS 기준 -> 윈도우는 명령어가 다름
```

![venv_active](/assets/img/2_venv_activate.png)

```shell
deactivate  # venv 비활성화
```

3. 가상환경에 Django 설치

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

1. Django 프로젝트 생성

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

2.
