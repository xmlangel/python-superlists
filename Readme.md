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

# 첫번째 기능테스트 코드 만들기
---
from selenium import webdriver

browser = webdriver.Firefox()
browser = get('http://localhost:8000')

assert 'Django' in browser.title
---
파이어폭스창을 실행하기 위해 셀레늄을 구동하고
브라우저를 통해 웹페이지를 연다.
title 에 Django 라는 단어가 있는지 확인한다.


