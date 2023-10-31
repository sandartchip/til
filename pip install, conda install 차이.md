
- pip install은 파이썬 패키지 관리를 통해 라이브러리 설치 및 패키지 관리를 함.
- conda install은 anaconda 패키지 관리를 통해 라이브러리 설치 및 관리를 함.

<img src="https://github.com/sandartchip/TIL/assets/15938354/3bba3974-0224-4bc1-b165-49a2c7e14b3e" width="500px"/>

​

~~### 1-1. conda deactive 상태, 일반 cmd상에서 pip로 설치한 경우~~
~~-> anaconda에서 관리하는 전역 pip 폴더에 설치됨.~~

~~저장위치 예시) /Users/사용자이름/anaconda3/env/py36/bin/pip~~

​
~~### 1-2. conda가 아닌 일반 cmd상에서 pip3로 설치한 경우​~~

~~-> local 내의 pip3에 들어감.
저장위치 예시) /usr/local/bin/pip3~~

-> pip(python2) 와 pip3(python3)가 달랐을 때의 글. 지금 서버에서는 pip와 pip3가 같아서 의미없어짐

### 1. conda 밖에서 pip install로 설치 
- /usr/local/lib/python3.8/dist-packages

### 2. conda 내에서, pip install로 설치한 경우
- 현재 activate된 가상환경에만 패키지를 설치.
- conda가 activate된 상태에서는 pip 명령어를 사용해도 conda 환경에 설치됨.

- 설치 위치
![image](https://github.com/sandartchip/TIL/assets/15938354/a32d3db1-e1bc-47d5-a932-ca642b65b9a4)

ex)

```
base-> /Users/사용자이름/anaconda3
py36 -> /Users/사용자이름/anaconda3/envs/py36
```

### 3. conda 내에서 conda install로 설치한 경우 
```
$ (py36) conda install jupyter
```
- 한 경우에는, Py36에만 jupyter가 설치되고, 그 외 다른 환경(예를 들면, base)에는 설치되지 않는다.
- pip install, conda install로 설치해도 설치 경로 차이X
- 다운받을 수 있는 패키지 차이. 속도는 pip가 더 빠른듯.

https://medium.com/analytics-vidhya/understand-conda-and-pip-9e5c67da47cc

​
