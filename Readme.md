리눅스와 맥OS

# git 초기화
git init

#venv 환경에서 작업
리눅스와 맥에서 virtualenv를 생성하려면 간단하게 python3 -m venv [이름]를 실행하면 됩니다.

python3 -m venv superlist-python

source ./superlist-python/bin/activate

# django 설치

\'
pip install django
\'

#.gitignore 파일만들기
'''
superlist-python/
db.sqlite3
.pyc
__pycache__
.DS_Store
'''

#selenium 설치

#requirements.txt 파일설치

'''
pip freeze > requirements.txt
'''

## 나중에 복구할때는 아래롸같이 하면 동일한 환경유지

'''
pip install -r requirements.txt
'''

#git addd & commit

'''
git add .
git commit -m '첫번째커밋
'''

#git hub 연결
'''
git remote add origin git@github.com:<your-github-username>/python-superlists.git
git push -u origin master
'''

# 설명파일 수정

# 첫번째 기능테스트 코드 만들기(project 폴더)
---
from selenium import webdriver

browser = webdriver.Firefox()

browser = get('http://localhost:8000')

assert 'Django' in browser.title

---
파이어폭스창을 실행하기 위해 셀레늄을 구동하고

브라우저를 통해 웹페이지를 연다.

title 에 Django 라는 단어가 있는지 확인한다.


# 코드실행 에러 확인

Traceback (most recent call last):
  File "functional_test.py", line 3, in <module>
    browser = webdriver.Firefox()
  File "/Users/Kwangmyung/private/git/python/superlist/superlist-python/lib/python3.5/site-packages/selenium/webdriver/firefox/webdriver.py", line 80, in __init__
    self.binary, timeout)
  File "/Users/Kwangmyung/private/git/python/superlist/superlist-python/lib/python3.5/site-packages/selenium/webdriver/firefox/extension_connection.py", line 52, in __init__
    self.binary.launch_browser(self.profile, timeout=timeout)
  File "/Users/Kwangmyung/private/git/python/superlist/superlist-python/lib/python3.5/site-packages/selenium/webdriver/firefox/firefox_binary.py", line 68, in launch_browser
    self._wait_until_connectable(timeout=timeout)
  File "/Users/Kwangmyung/private/git/python/superlist/superlist-python/lib/python3.5/site-packages/selenium/webdriver/firefox/firefox_binary.py", line 108, in _wait_until_connectable
    % (self.profile.path))
selenium.common.exceptions.WebDriverException: Message: Can't load the profile. Profile Dir: /var/folders/kd/9skj88w508gf1k0rq6fmg04w0000gn/T/tmp8sj5ekhj If you specified a log_file in the FirefoxBinary constructor, check it for details.

# 잘못된부분 수정 browser 를 통해서 하는 부분오타
---
from selenium import webdriver

browser = webdriver.Firefox()

browser.get('http://localhost:8000')

assert 'Django' in browser.title

#다시실행(project 폴더)
python functional_test.py

#Firefox 드라이버는 실행안되는듯해서 chrome 드라이버로 변경 코드수정

from selenium import webdriver

browser = webdriver.Chrome('./chromedriver')

browser.get('http://localhost:8000')

assert 'Django' in browser.title

# 당연히 실패 현재 장고를 띄워놓지 않아서.
Traceback (most recent call last):
  File "functional_test.py", line 7, in <module>
    assert 'Django' in browser.title
AssertionError

#장고실행로 프로잭트생성(project 폴더에서 실행)
django-admin.py startproject superlists

# 트리구조확인.
├── chromedriver
├── chromedriver_mac64.zip
├── functional_test.py
└── superlists
    ├── manage.py
    └── superlists
        ├── __init__.py
        ├── settings.py
        ├── urls.py
        └── wsgi.py

# 장고실행
장고실행은 manage.py 를 통해서 이루어진다. 대부분 장고의 명령어들은 manage.py 를 통해 이루어짐.

python manage.py runserver

# 기능테스트 다시실행
정상실행 됨 당연한결과