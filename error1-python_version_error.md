
```
ModuleNotFoundError: No module named ‘apt_pkg’

 File "/usr/lib/python3/dist-packages/CommandNotFound/db/db.py", line 5, in <module>
    import apt_pkg
```

=> 현재 v가 실행하는 프로그램은 python3 버전을 실행하도록 미리 세팅되어 있다.

현재, python3 파일은 내용이 없고 symlink로 python3.7과 연결되어 있다.


```
sudo update-alternatives --config python3
```


