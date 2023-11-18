
- 원리는 아직 정확히 파악 못함.
- double fork를 하는 이유는 포크된 데몬 프로세스를 부모 프로세스로부터 완전히 분리하고, 세션으로부터 떨어지도록 하기 위해서라고 함. 


```python

    # double fork, first fork
    pid = os.fork()
    if pid > 0:
        # parent procrss
        # just exit
        exit(0)
    else:
        # decouple from parent envronment
        os.chdir('/')
        os.setsid()
        os.umask(0)

        # second fork
        pid = os.fork()
        if pid > 0:
            exit(0)
        else:
            sys.stdout.flush()
            sys.stderr.flush()

            si = open(os.devnull, 'r')
            so = open(os.devnull, 'a+')
            se = open(os.devnull, 'a+')

            os.dup2(si.fileno(), sys.stdin.fileno())
            os.dup2(so.fileno(), sys.stdout.fileno())
            os.dup2(se.fileno(), sys.stderr.fileno())

            with open(args.pid, "w") as pid_file:
                pid_file.write(str(os.getpid()))

            singing_miku = SingingMiku(args.log)
            exit_code = singing_miku.main()
            exit(exit_code)
```

#### 참고자료
https://medium.com/@HatusneMiku3939/%EB%A6%AC%EB%88%85%EC%8A%A4-%EB%8D%B0%EB%AA%AC-%EB%A7%8C%EB%93%A4%EA%B8%B0-python-1-3c5ea10c6366
