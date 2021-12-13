

# pyenv
![image](https://user-images.githubusercontent.com/15938354/144147393-c1422462-162c-490a-8119-e51c6ec14a3c.png)

- 파이썬 버전을 관리하는 툴.
- 하나의 컴퓨터에 다양한 파이썬 버전을 설치하고 관리.
- pyenv로 여러 버전 파이썬 설치, pyenv-virtualenv로 여러 버전의 가상 환경 만들기, autoenv로 가상환경 자동 실행, pip로 가상환경에 파이썬 패키지 설치.
- 삼각형 위쪽의 커맨드부터 순서대로 읽힌다.
- 공식 깃허브 : https://github.com/pyenv/pyenv-installer

#### 의존 라이브러리들 
```
sudo apt-get install -y make build-essential \
 libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev \
 wget curl llvm libncurses5-dev libncursesw5-dev \
 xz-utils tk-dev git python-pip
```

```
sudo apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git
```

#### 설치 

- github에서 다운로드 후 bash로 실행
```
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```

.bash_profile
- profile에 넣어도 되지만, bash 쉘이 쓰이기 때문에 bash_profile에 
- profile파일에 환경변수 관련 세팅, alias는 bashrc에 주로 넣으므로, .profile에 세팅 
 
```
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"

```

그런데 ubuntu에서 pyenv 명령어로 시스템 python 버전이 안바뀌는 문제가 생겨서..
여러개의 각각 다른 파이썬 버전은 shims폴더에 있음.
따라서 그 폴더 경로도 profile상의 PATH에 넣어줘야함
export PATH="$PYENV_ROOT/shims:$PATH"

마지막으로, pyenv와 virtialenv를 초기화 함. 
```
eval "$(pyenv init -)"            # 쉘에 pyenv를 로드하는 과정
eval "$(pyenv virtualenv-init -)" # 쉘에 virtualenv를 로드하는 과정 
```
둘을 초기화하지 않으면 쉘에서 pyenv와 virtualenv를 사용 불가




### pyenv-virtualenv
- virtualenv은 파이썬 환경을 격리하는 툴.
- pyenv-virtualenv은 virtualenv의 pyenv 확장 플러그인.
- 파이썬 버전과 라이브러리의 완전한 격리 환경을 제공.
- pyenv를 pyenv-installer로 설치할 때 pyenv-virtualenv 설치가 포함됨. 이후 bashrc에서 초기화시킴 

### autoenv
- 특정 폴더에 들어오면 특정 가상환경 실행하도록 자동 세팅
- bashrc에 다음과 같이 작성
```shell

source ~/.autoenv/activate.sh 
```
- .env파일에 다음과 같은 내용을 작성함

```shell
echo “***********************************”
echo “Python Virtual Env > dero_env”
echo “***********************************”

pyenv shell dero_env 
pyenv activate
```


- 특정 프로젝트 폴더로 들어가면 .env파일 실행하여 가상환경 활성화.



## 현재 
- 안됨..-ㅁ-
- pyenv gloal local 명령어로 파이썬 버전이 바껴야하는데 안 바뀜.

#### 참고
- pyenv가 python을 올바르게 설치하려면 Python 빌드 종속성을 설치해야 합니다. 새로운 파이썬 버전. python 또는 pip와 같은 명령을 실행할 때 운영 체제는 디렉터리 목록을 검색하여 해당 이름의 실행 파일을 찾습니다. 이 디렉토리 목록은 PATH라는 환경 변수에 있으며 목록의 각 디렉토리는 콜론으로 구분됩니다.


### 참고자료 
https://wikidocs.net/10936
http://taewan.kim/post/python_virtual_env/

### OpenSuse 에서 설치
https://gist.github.com/antivanov/01ed4eac2d7486a170be598b5a0a4ac7
