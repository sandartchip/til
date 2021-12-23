



```yml

version: '3.1'
services:
  maria_db:
    image:
    ports:
    - "3306:3306"
    volumes:
    - 도커의 폴더 경로:호스트의 폴더 경로 
    environment:
      -MYSQL_ROOT_PASSWORD= ???
      -TZ="Asia/Seoul"
    
    
   
```

MYSQL_ROOT_PASSWORD 
root 계정의 패스워드를 mariadb로 지정 
