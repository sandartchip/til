* 윈도우에선 이 방법)
https://firstquarter.tistory.com/entry/Git-%ED%86%A0%ED%81%B0-%EC%9D%B8%EC%A6%9D-%EB%A1%9C%EA%B7%B8%EC%9D%B8-remote-Support-for-password-authentication-was-removed-on-August-13-2021-Please-use-a-personal-access-token-instead


# 1번 방법 (잘됨)

```
git config credential.helper store

# 로그인 정보를 등록하기 위한 push, 변경점이 없어도 push가 됨
git push 자동로그인하고싶은저장소주소

- 꼭 push 아니라도, pull이나 fetch 등 원격서버 접속 필요한 작업 하면 됨

# ex. 내가 자동 로그인을 하고싶은 git 주소가 https://example.github.com 이라면
# git push https://example.github.com 라고 입력

# 나오는 과정을 따라하면 됨, email, password를 입력
# 모든 과정이 끝나면 아래의 사진같은 모습이 나오며 push를 할때마다 로그인을 할 필요가 없어짐
```
- credential.helper store 옵션을 주면 인증 절차를 생략할 수 있어 한결 편리하다. 물론 최초 한번의 인증 절차는 필요하다.

-https://daechu.tistory.com/33

# 2번 방법 (잘안됨)
- AWS에 git-credential 파일이 안보임..

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

