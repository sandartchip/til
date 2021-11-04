
# step 1
- 파이참에서 작업중인 프로젝트의 최상위 경로에 .gitignore 파일 생성 (브라우저의 git에서)

# step 2
- gitignore 파일 내용 작성

```
venv/
.idea/
db.sqlite3
<MY-PROJECT-DIRECTORY>/settings.py
 
# temporary files
*.log
*.pot
*.pyc
__pycache__/
```

# step 3
- 이미 git에서 트래킹하는 파일은 재적용 시키기 
- 기존에 커밋 안된 내용 있으면 커밋시키고
- git pull 로 리모트 git 리포지토리에 추가된 gitignore 파일 pull로 가져옴 
- 기존의 git 에서 트래킹 중인 파일들 목록 캐시 제거 (git https://github.com/sandartchip/TIL/blob/main/GIT/gitignore%20%EC%A0%81%EC%9A%A9.md )
- git add, commit, push 다시 하면, git ignore이 재적용됨


https://onlytojay.medium.com/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%ED%8C%A8%ED%82%A4%EC%A7%80%EC%97%90-gitignore-%ED%8C%8C%EC%9D%BC-%EC%B6%94%EA%B0%80%ED%95%98%EA%B8%B0-e0daf338a8d0



### 참고자료)
- https://opentutorials.org/course/3666/24539
