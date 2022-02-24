



## pyenv

```shell
# pyenv 설치 (https://github.com/pyenv/pyenv)
$ brew install pyenv

# 환경 변수 설정
$ echo -e '\nif command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi' >> ~/.zshrc

# zshrc 재실행
$ source ~/.zshrc

# install 가능한 파이썬 목록
$ pyenv install --list  

# 특정 파이썬 버전 설치
$ pyenv install 3.8.12

# 현재 설치된 파이썬 버전 확인
$ pyenv versions

# 현재 사용중인 파이썬 버전 확인
$ pyenv version

# 가상환경 만들기
$ pyenv virtualenv 3.8.12 spo

# 가상환경 삭제
$ pyenv uninstall spo
```



## poetry

```shell
# poetry 설치 (https://python-poetry.org/docs/#installation)
$ curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -

# 환경 변수 설정
$ echo -e 'export PATH="$HOME/.poetry/bin:$PATH"' >> ~/.zshrc

# zshrc 재실행
$ source ~/.zshrc

# poetry 입력 후 tab 누르면 명령어 목록 뜨는 기능
$ mkdir $ZSH_CUSTOM/plugins/poetry
$ poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry

# 프로젝트 내부에 .venv 디렉토리 생성하는 설정
$ poetry config virtualenvs.in-project true

# 현재 폴더에서 poetry 초기화 (엔터 눌러서 전부 default로 설정)
$ poetry init

# 패키지 추가 (개발 환경에서만 사용할 패키지 따로 설치)
$ poetry add pandas (-D)

# 패키지 확인 (의존성 확인) (개발 환경 패키지 제외)
$ poetry show (--tree) (--no-dev)

# 패키지 삭제
$ poetry remove pandas

# 가상 환경 들어가기 (패키지 추가가 에러나면 가상 환경 들어와서 pip로 설치)
$ poetry shell

# 가상 환경 나오기
$ exit

# build (소스를 배포가능한 형태로 빌드) - "poetry new 프로젝트명" 명령어로 생성시에만 가능
$ poetry build

# requirements.txt 추출
$ poetry export -f requirements.txt > requirements.txt
```



### 기타

```shell
# requirements.txt로 설치
$ pip install -r requirements.txt
```

