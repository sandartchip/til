
#### Dumpdata
```python
python manage.py dumpdata > xxx.json
```

``` python
python3 manage.py dumpdata --exclude auth.permission --exclude authtoken --exclude contenttypes > 2018-11-29.json
```

덤프할 때 필요없는 데이터베이스는 제외하고.

##### 특정 테이블만
```
python manage.py dumpdata 앱이름.특정테이블 > data.json 
```

#### Loaddata
```
python3 manage.py loaddata 덤프파일 있는 앱명/fixtures/덤프파일.json
```



https://realcoding.tistory.com/2
