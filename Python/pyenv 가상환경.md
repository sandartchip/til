
![image](https://user-images.githubusercontent.com/15938354/144147393-c1422462-162c-490a-8119-e51c6ec14a3c.png)

- pyenv로 여러 버전 파이썬 설치, pyenv-virtualenv로 여러 버전의 가상 환경 만들기, autoenv로 가상환경 자동 실행, pip로 가상환경에 파이썬 패키지 설치.

### pyenv
- 파이썬 버전을 관리하는 툴.
- 하나의 컴퓨터에 다양한 파이썬 버전을 설치하고 관리.

### pyenv-virtualenv
- virtualenv은 파이썬 환경을 격리하는 툴.
- pyenv-virtualenv은 virtualenv의 pyenv 확장 플러그인.
- 파이썬 버전과 라이브러리의 완전한 격리 환경을 제공.
- pyenv를 pyenv-installer로 설치할 때 pyenv-virtualenv 설치가 포함됨. 이후 bashrc에서 초기화시킴 

bashrc
```
eval "$(pyenv virtualenv-init -)"

```

### autoenv
- pyenv-virtualenv 사용 시 불편한 수작업을 자동화.
- 특정 프로젝트 폴더로 들어가면 .env파일 실행하여 가상환경 활성화.

