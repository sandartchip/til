
로컬 작업 본 폐기 하고 원격 작업본 가져오려면..


```
git fetch --all
git reset --hard origin/main # git reset은 포인터를 특정 위치로 옮기는 명령어. hard 옵션 추가-> 그 커밋 이후 내용들은 삭제돔. --mixed 옵션 -> 변경 이력 모두 삭제 되나, 스테이지에 코드가 남아있음. -
-커밋 히스토리

git pull origin main
```


강제로 push하려면 (하지마-_-;;;;;;;; 이렇게 하다 망했음..)
```
git push -u origin master --force
```
