
```
Large files detected. You may want to try Git Large File Storage 
```

-> 현재, 이 에러가 뜨면서 push가 안 된다.

현재 파일은 지워진 상태.

**해결법1. git init으로 git 초기화 한 후 재 커밋, 재 푸쉬**
```
git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch 에러가 난 파일명'
```
-> 해결X

**해결법2. 파일의 캐쉬 삭제**

```
Removing sensitive data from Git. “fatal: ambiguous argument 'rm'”
```


=> single quote(')을 "으로 바꾸니 해결 
```
git filter-branch -f --index-filter "git rm --cached --ignore-unmatch 에러가 난 파일명"

```

=> 삭제해야하는, fastq.gz을 한꺼번에 삭제 후 해결.

```

git filter-branch -f --index-filter "git rm --cached --ignore-unmatch  *.fastq.gz"

```

오랜시간 push를 못하게 한 대용량 파일 문제가 해결됨.



> 또 다시 하니, 
```
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
``` 

문제가 발생함

```
git pull origin master --allow-unrelated-histories
```
엉킨 히스토리를 무시하고 pull했기 때문에 master 브랜치와 다른 원격저장소의 파일의 충돌이 나서, RESET >>>> 등의 기호가 파일에 적힌다.
=> 일단은 pull하고, 백업한 원본 파일을 다시 붙여넣음.

충돌을 모두 해결한뒤 commit, push 를 하면 된다.

=> 이렇게 해결되긴 했는데 이게 정말 최선인가..
