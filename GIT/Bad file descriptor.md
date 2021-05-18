
```
error: Could not read 164d5e5aab514a74463b7d096583c204f5caa6d2
fatal: bad tree object 164d5e5aab514a74463b7d096583c204f5caa6d2
fatal: The remote end hung up unexpectedly
fatal: The remote end hung up unexpectedly
error: failed to push some refs to 'https://github.com/sandartchip/serotype_v2.git'
fatal: write error: Bad file descriptor
```




이거도 큰 파일 올리다 생긴 에러임.

파일 때문인건 알겠는데 정확한 원인은 모르겠음.


### stackoverflow 
> git config --global pack.windowMemory "32m".


버퍼사이즈 늘리기 
> git config http.postBuffer 524288000

둘 다 안되고..

결국 
1. git 폴더 초기화하고,
 > rm -rf .git
 > git init

이하 커밋 등 기존 절차 밟은 후 
 
3. gitignore에 /media 폴더 추가, 
4. gitignore 반영시키고 다시하니 media 폴더가 git에서 처리안됨-> Large file 에러 해결



