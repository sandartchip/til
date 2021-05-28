

대용량 파일 업로드할 떄 발생하는 에러다. 

```
git add .gitignore
git commit -m "[ADD] Git ignore files"
git push
```

.gitignore 파일에 추가해도 large file 에러가 해결이 안될 때
파일이 올라간 git의 캐시 자체를 삭제함


### A.1 
```
git rm -r --cached .
git add .
git commit -m "[MOD]Activate .gitignore file"
```

대용량 파일들을 git에서 적용시키지 않게 하기 위해 캐시 삭제.

=> 이걸 해도 안 된다...??!

### A.2
```
git config --global --unset http.postBuffer
git config --global http.postBuffer 1048576000
```
=> 해도 해결 X


### A.3 
```
git remote remove origin
git remote add origin https://github..com/user/repo
git push --set-upstream origin master
```
