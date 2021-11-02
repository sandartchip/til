
## 유저 계정 생성
- 가입 계정은 루트 계정. 모든 권한을 가지고 있음
- 보안이 뚫릴 경우 공격자가 모든 권한을 가지는 문제 생김 -> 유저 계정 생성해야 함.
- 링크 : https://console.aws.amazon.com/iamv2/home#/users

## 키페어 생성
- AWS는 공개키 암호화 방식을 이용하여 로그인 정보를 암호화 및 해독한다.


## 인스턴스
- 인스턴스 : AWS에서 제공하는 가상 컴퓨팅 환경 (컴퓨터)

## 접속
- EC2 퍼블릭 ip4 주소로 접속 


## Django와 연결
- 장고는 웹 서버와 직접 통신할 수 없어서 둘 사이에 WSGI를 두어야 한다.
- 이를 위해 uWSGI 라는 패키지를 설치해서 Django와 연결.
- 기존 프로젝트의 requirements.txt 패키지 설치 
(참고) https://nerogarret.tistory.com/47

#### mysql 설치 에러 발생 시
- https://velog.io/@sandartchip/Command-errored-out-with-exit-status-1-python-setup.py-egginfo-Check-the-logs-for-full-command-output
- https://mirae-kim.tistory.com/73



#### Django 프로젝트 실행 
python3 manage.py runserver 0:8000

```
django.db.utils.OperationalError: (1698, "Access denied for user 'root'@'localhost'")
```
에러 발생 -> 원인: mysql의 비번과 django에서 설정한 db 비번이 다름

##### 해결
- https://velog.io/@hong_tae/mysqlclient-ubuntu20.04-%EC%8B%A4%ED%96%89-%EC%B0%A9%EC%98%A4-NameError-name-mysql-is-not-defined
