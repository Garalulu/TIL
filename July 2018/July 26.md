# Django

## Django project

가상 환경 안에서 모든 작업을 해야 한다.

가상 환경 사용 명령어
```
myvenv\Script\activate
```


프로젝트 생성
```
(myvenv) C:\Users\pak\djangogirls>django-admin.py startproject mysite .
```

다음과 같은 디렉토리가 생성된다.

```
djangogirls
├───manage.py
└───mysite
        settings.py
        urls.py
        wsgi.py
        __init__.py
```
manage.py : 사이트 관리를 도와주는 스크립트  
settings.py : 웹사이트 설정  
urls.py : urlresolver가 사용하는 패턴 목록

mysite/settings.py 수정  
수정은 Atom을 이용했다.

```
TIME_ZONE = 'Asia/Seoul' # 웹사이트 시간
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static') # 정적 파일 경로 추가
ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com'] # 호스트 설정
```

데이터베이스 설정

사이트 내 데이터를 저장하기 위한 다양한 데이터베이스 소프트웨어 중 sqlite3을 사용할 것이다.

블로그에 데이터베이스 생성
```
python manage.py migrate
```

django 1.11 깔았더니 SyntaxError 떠서 2.0으로 업그레이드 했다.

웹 서버 시작
```
python manage.py runserver
```

```
http://127.0.0.1:8000/
```
웹 서버가 실행되는 동안 추가 명령을 입력하려면 새 터미널 창을 열고 virtualenv를 활성화해야 한다.  
웹 서버를 중지하려면 Ctrl + Break를 누른다.