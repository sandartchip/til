# dockerd
```
dockerd is the persistent process that manages containers
```
컨테이너를 관리하는 백그라운드 프로세스, 즉 도커 데몬. 


# Volume

- 호스트 저장공간과 도커의 저장공간 연결 


## 루트에 볼륨 생기는 경우

```Dockerfile
# Dockerfile

FROM ubuntu:latest

volume ["/volume/path"]

```

으로 볼륨을 선언하고 이미지를 
빌드하여 이미지 생성하면
run 되어 컨테이너로 올라갈 때 자동으로 
/var/lib/docker/volumes/{volume_name} 에 만들어짐

### Dockerfile 실행 후의, 볼륨 폴더 예시>

```
cd /var/lib/docker/volumes && ls 

37c37549f7eff63aec8a56c42707a109dc7adb108926412848e4c268574d747d  metadata.db
```

## Docker run할 때 볼륨 매핑

```
  docker run -itd -v /host/some/where:/container/some/where ubuntu
```

- 장점: 직관적으로 호스트의 파일시스템과 컨테이너의 파일 시스템이 매핑.
- 단점: docker volume ls등의 명령어로 추적 안됨
