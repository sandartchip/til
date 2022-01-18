

- nginx 도커 내부에서 service nginx stop 해도 도커 컨테이너 자체가 종료 되어버림.
- nginx 컨테이너는 다른 컨테이너에 nginx 깔린게 아니라 nginx 자체이기 때문에 nginx을 종료 시키면 컨테이너 자체가 종료됨. 
