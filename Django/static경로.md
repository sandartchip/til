

settings.py에 

- STATIC_URL 
```python
STATIC_URL = '/static/'
```


클라이언트로부터 페이지에 대한 요청이 왔을 때, 

{% static 'img/sample.jpg' %}로, 태그가 있으면, 

runserver는 STATIC_URL + '경로'로 바꾸어 렌더링

-> /static/img/sample.jpg 


## STATICFILES_DIRS

STATICFILES_DIRS = [
 '/var/www/static', 
]

- 특정 앱에 연결되지 않은 static 파일들. 
- static 경로가 어딘지 설정함. 
- 개발할 때 STATICFILES_DIR에 등록된 실제 경로에서 해당 정적파일 탐색. 


STATICFILES 
runserver는, settings.py에 등록된 STATIC_URL과 STATICFILES_DIR을 

## STATIC_ROOT 
- 배포 할 때만 사용함. 
 

https://cupjoo.tistory.com/116

