
로컬 작업 본 폐기 하고 원격 작업 가져오려면..


```
git fetch --all
git reset --hard origin/main
git pull origin main
```


강제로 push하려면
```
git push -u origin master --force
```
