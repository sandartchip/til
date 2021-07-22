git ignore은 고정이 아니라, 커밋에 따라 변경사항이 계속 바뀐다.


### git ignore파일에 들어가야 할 항목

1. 임시 리소스 
(캐시 파일, 로그 파일, 컴파일 된 코드 등)

2. 다른 개발자들과 공유할 필요 없는 로컬 설정 파일들 

3. 로그인 암호나 키 등의 민감 정보 파일 

- git 저장소의 최상위 디렉토리에 해당 파일이 존재할 경우, 파일 내에 기술된 규칙은 전체 저장소의 모든 파일들과 서브 디렉토리들에 **재귀적으로** 적용됨. 
-> 즉, /__pycache__/라고 적어놨을 경우 /앱/__pycache__/와 /__pycache__/가 모두 git 에서 무시됨.

```.gitignore

file.txt

# file.txt라는 이름을 ignore 시킨다. 파일 명만 기술된 경우, 최상위 디렉토리 뿐만 아니라 모든 서브 디렉토리에 동일하게 적용.
파일 하부의 어디에 있던 모두 ignore 처리 될 것이다.

bin
# bin이라는 폴더와 bin이라는 파일 ignore 처리

bin/ 
# 디렉토리 전체 ignore처리
# 현재 경로의 디렉토리만.


# 모든 위치에서의 디렉토리를 ignore 처리 하고싶다면
**/디렉토리명/

#예시)

**/bin/

# 은,
# bin/
# mine/bin/
# /mine/mine2/bin/

모두 ignore처리 함.

```

### gitignore은 대소문자 구분 못한다. 
- Program 폴더와 program 폴더를 동일하게 인식 함.
-> git 설정에서 대소문자 구분 하라고 설정해야 함 

(아래 명령어를 수행하라)
```
git config core.ignorecase false
```

#### 이미 push된 프로젝트 .gitignore 재적용 시키기 

```
git rm -r --cached .
git add . 
git commit -m "커밋메세지"
git push origin {브랜치명}
```

#### 원격 서버 내용 강제로 pull받아오기 

```
 git reset --hard origin/main
```

참고) https://nochoco-lee.tistory.com/46
