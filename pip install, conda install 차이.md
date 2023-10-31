pip install은 파이썬 패키지 관리를 통해 라이브러리 설치 및 패키지 관리를 함.

​

conda install은 anaconda 패키지 관리를 통해 라이브러리 설치 및 관리를 함.

​

### 1-1. conda가 아닌 일반 cmd상에서 pip로 설치한 경우

-> anaconda에서 관리하는 전역 pip 폴더에 설치됨.


저장위치 예시) /Users/사용자이름/anaconda3/env/py36/bin/pip

​
### 1-2. conda가 아닌 일반 cmd상에서 pip3로 설치한 경우​

-> local 내의 pip3에 들어감.
저장위치 예시) /usr/local/bin/pip3


### 2. conda 내에서, pip install로 설치한 경우
- 현재 activate된 가상환경에만 패키지를 설치. 

ex)

base-> /Users/사용자이름/anaconda3

py36 -> /Users/사용자이름/anaconda3/envs/py36

​

$ (py36) conda install jupyter 

​

한 경우에는, Py36에만 jupyter가 설치되고, 그 외 다른 환경(예를 들면, base)에는 설치되지 않는다.

​

pip install, conda install로 설치해도 설치 경로 차이X

​

다운받을 수 있는 패키지 차이. 속도는 pip가 더 빠른듯.

​

​

​
