

대용량 파일 업로드할 떄 발생하는 에러다. 

```
git add .gitignore
git commit -m "[ADD] Git ignore files"
git push
```

## 1. media 디렉토리 무시
```
media/
```

## 2. "*.fastq" 확장자 무시
```
*.fastq
```

## 3. sam.fastq 파일 무시 
```
sam.fastq
```



## 주의사항  : 기존에 git의 관리를 받고 있던 파일이나 폴더 경로를 .gitignore 파일에 추가로 작성하고 push 해도 무시되지 않음

.gitignore 파일에 추가해도 large file 에러가 해결이 안될 때
=> 용량이 큰 파일을 커밋 캐시에서 삭제하여 커밋 하지 않도록 한다. 


### A.1 
```
git rm -r --cached .  
git add .
git commit -m "[MOD]Activate .gitignore file"
```

### media 디렉토리 무시 

```
git rm --cached media/ -r 
```
#### 위의 gitignore과 동일한 형태로 써주면 됨.

혹은, 

```
 git filter-branch --index-filter 'git rm -r --cached --ignore-unmatch 캐시삭제할 용량큰 파일명' HEAD
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


==> 이 모든걸 했는데 
```
 pack exceeds maximum allowed size
```
가 떴다.
