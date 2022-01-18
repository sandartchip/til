

도커 컴포즈 & nginx로 배포할 때 주의점은 

```yml

nginx:
        image: nginx:latest
        container_name: nginx

        volumes:
                - ./nginx:/etc/nginx/conf.d
                - ./프로젝트명/collected_statics:/staticfiles

```

장고의 collectstatic 폴더를 nginx 컨테이너와 볼륨으로 연결함.

https://nerogarret.tistory.com/48
