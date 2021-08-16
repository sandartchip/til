

- https://db2dev.tistory.com/entry/Git-%EA%B9%83%ED%97%88%EB%B8%8C-personal-access-token%EC%9C%BC%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%98%EA%B8%B0


1. 
```
git config --global --unset credential.helper
```
로 git 계정 세팅 초기화 

2. ~/.git-credential의 비밀번호 정보를 token 정보로 바꿔둠

3. 
```
git config --global credential.helper store 
```


