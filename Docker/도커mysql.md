



```yml

# docker-compose.yml 

version: '3.1'
services:
  maria_db:
    image: mariadb:latest 
    container_name: "mariadb"
    restart: always
    ports: 
    - "3306(호스트의 포트):3306(도커 컨테이너의 포트)"
    volumes:
    - 호스트의 폴더 경로:컨테이너의 폴더 경로 
    environment:
      -MYSQL_ROOT_PASSWORD=test
      -TZ="Asia/Seoul"
    
    
   
```

MYSQL_ROOT_PASSWORD 
root 계정의 패스워드를 mariadb로 지정 
