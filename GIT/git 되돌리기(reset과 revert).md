
## reset
reset - > 커밋 이력이 삭제됨. 

### reset --hard
- 커밋이 없어짐 
- 이전 버전으로 파일들이 돌아감

### reset --soft
- 내 컴퓨터의 파일 자체는 안 바뀜 
- 커밋만 이전으로 돌아감
- staging area 안바뀜

### reset --mixed 
- 내 컴퓨터의 파일 자체는 안 바뀜
- 커밋은 이전으로 돌아감
- staging area  파일은 이전으로 돌아감

### reset --hard 
- **내 컴퓨터 파일이 바뀜** 
  -> 현재 작업중인 파일들 커밋 안했으면 날아갈 수 있음.
- 커밋은 이전으로 돌아감 (reset 시점 이후 새로 한 커밋은 없어짐)
- staging area 파일 역시 이전으로 돌아감 



## revert
revert -> 현재의 이력을 남기고 과거로 돌아감.


### revert 취소하기

1. git reflog   
2. git reset --hard 돌아가고싶은 로그번호 
