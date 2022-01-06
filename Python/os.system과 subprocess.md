

### os.system
- os.system은 **현재의 프로세스**에서 작업 후, 해당 명령어가 완료될 때 까지 기다린다.
- subprocess.popen()은 fork처럼 하나의 새로운 프로세스를 생성하고 작업하기 때문에, 기존 프로세스에 영향을 끼치지 않는다.

### subprocess
- subprocess 모듈은 파이썬 프로그램 내에서 새로운 프로세스를 스폰하고 여기에 입출력 파이프를 연결하며 리턴코드를 획득할 수 있도록 하는 모듈로, 
- 다른 언어로 만들어진 프로그램을 통합, 제어할 수 있게 만드는 모듈이다. 이 모듈은 기존에 오랜된 몇몇 모듈과 함수(os.system, os.spawn*)들을 대체하기 위해 만들어졌다. (혹은 os.popen 같은 함수도…)

https://soooprmx.com/python-subprocess-1/
