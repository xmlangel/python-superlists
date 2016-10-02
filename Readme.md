리눅스와 맥OS

#venv 환경에서 작업
리눅스와 맥에서 virtualenv를 생성하려면 간단하게 python3 -m venv [이름]를 실행하면 됩니다.

python3 -m venv superlist-python

source ./superlist-python/bin/activate

# django 설치
pip install django


make git .gitignore

superlist-python/
db.sqlite3
.pyc

#selenium 설치

#requirements.txt 파일설치

pip freeze > requirements.txt

## 나중에 복구할때는 아래롸같이 하면 동일한 환경유지

pip install -r requirements.txt

