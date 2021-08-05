## 현상

원격서버에 도커 이미지 다운받아 만든 mysql에 접속이 안 되기 시작 함.

## 시도해 본 방법

1. 도커 내의 Mysql 쉘에 접속해서 SHOW PROCESSLIST 수행, 딜레이 된 프로세스 있나 확인
-> 없음

2. 
![image](https://user-images.githubusercontent.com/15938354/128285456-ef5ff663-5542-4661-8230-c8871ecb038e.png)
->  root계정이 모든 IP대역에서 접속 가능한지 확인
-> User가 root일 때 HOST는 %  세팅 되어 있음.

3. 
![image](https://user-images.githubusercontent.com/15938354/128286482-1d2f3014-36f1-4473-becf-43910533fff0.png)
