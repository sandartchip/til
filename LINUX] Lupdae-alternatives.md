

### update-alternatives?

우분투를 설치하면 python path가 2.7로 설정되어 있다. 

Alternatives는 기본 커맨드의 symbolic 링크를 관리해준다. 


```
ls -al /usr/bin/python
```
으로 어떤 파일을 가리키는지 확인 가능하다. 

-> 현재 파일이 없다. 

/usr/bin/python => /usr/bin/python3.7을 가리키도록 변경해야 한다. 


### Update-alternatives로 파이썬 버전 등록 및 변경

- 먼저, 파이썬을 등록하기 전에 이미 등록된 것이 있는지 확인해야 함. 
- 



출처: https://codechacha.com/ko/change-python-version/#:~:text=update-alternatives%20--config%20python,%EB%90%9C%20%EA%B2%83%EC%9D%B4%20%EC%97%86%EB%8B%A4%EB%8A%94%20%EC%9D%98%EB%AF%B8%EC%9E%85%EB%8B%88%EB%8B%A4.&text=%EB%AC%BC%EB%A1%A0%20%ED%8C%8C%EC%9D%B4%EC%8D%AC%202.7%EA%B3%BC%203.6%EC%9D%B4%20%EC%84%A4%EC%B9%98%EB%90%98%EC%96%B4%20%EC%9E%88%EC%96%B4%EC%95%BC%20%ED%95%A9%EB%8B%88%EB%8B%A4.
