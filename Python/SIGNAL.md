
### SIGTERM
- 프로세스에게 종료를 부탁하는 의미로 생각할 수 있음.
- 이 signal을 받은 프로세스는 처리를 마무리하고 정상 종료해야 하기 때문에 graceful shutdown에 적합합니다. docker stop과 kubectl delete pod 모두 즉시 SIGTERM을 보냅니다.

### SIGKILL
프로세스에게 시간을 주지 않고 즉시 종료할 때 사용합니다. docker kill을 실행하면 컨테이너에 즉시 SIGKILL을 보냅니다. docker stop과 kubectl delete pod 모두 처음에는 SIGTERM을 보내지만, 만약 CLI에서 설정한 시간 동안 프로세스가 종료되지 않으면 SIGKILL을 다시 보내서 즉시 종료합니다.

### SIGINT
위에서 설명한 것처럼 터미널에서 프로세스를 종료하고자 Ctrl + C를 입력할 때 사용됨. 
Docker나 Kubernetes에서 이 시그널이 활용되진 않지만, 로컬에서 개발할 때 자주 사용하기도 합니다. gunicorn에서 즉시 종료할 때 사용되기도 합니다.

### signal handler
signal이 발생했을 때 실행할 코드를 의미합니다. OS에서 소유하는 default signal handler라는 게 있고, signal 종류마다 서로 다른 handler를 가지고 있습니다. 예를 들어 SIGKILL의 default signal handler는 프로세스를 종료시키는 동작을 합니다. 프로세스가 직접 자신만을 위한 signal handler를 정의할 수 있는데, 이것을 user defined signal handler라고 합니다. OS는 해당 프로세스에 user defined handler가 있으면 그것을 실행하고, 없다면 default handler를 실행합니다. 단 두 가지 예외가 있는데, SIGKILL과 SIGSTOP은 항상 default handler가 사용됩니다.




https://tech.buzzvil.com/blog/asyncio-no-3-sigterm/
