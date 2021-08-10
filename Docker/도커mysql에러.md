```
Authentication plugin ‘caching_sha2_password’ cannot be loaded:
```

- MYSQL8 이상에서는 사용자 계정 암호 설정을 할 때, SHA256 방식으로 함. 

- caching_SHA2_password는 authentication 시에 서버 측에서 캐싱을 하기 위한 모듈임.

- 그러나, 현재 대부분의 MYSQL Client는 caching_sha2_password 모듈이 존재 X


도커 생성 시 

```
--default-authentication-plugin=mysql_native_password
```

옵션 추가해서 기본 authentication 설정 바꾸면 이전 버전 MYSQL 처럼 접속 가능. 
