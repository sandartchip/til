
# 1번 방법

```
git config credential.helper store

# 로그인 정보를 등록하기 위한 push, 변경점이 없어도 push가 됨
git push 자동로그인하고싶은저장소주소

# ex. 내가 자동 로그인을 하고싶은 git 주소가 https://example.github.com 이라면
# git push https://example.github.com 라고 입력

# 나오는 과정을 따라하면 됨, email, password를 입력
# 모든 과정이 끝나면 아래의 사진같은 모습이 나오며 push를 할때마다 로그인을 할 필요가 없어짐
```

-https://daechu.tistory.com/33

# 2번 방법 (잘안됨)
1. 
```
git config --global --unset credential.helper
```
로 git 계정 세팅 초기화 

2. ~/.git-credential의 비밀번호 정보를 token 정보로 바꿔둠
```
http://github id:access%20token@github.com/
```

3. 
```
git config --global credential.helper store 
```



- https://db2dev.tistory.com/entry/Git-%EA%B9%83%ED%97%88%EB%B8%8C-personal-access-token%EC%9C%BC%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%98%EA%B8%B0

