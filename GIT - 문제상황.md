
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

