
# Djangos와 static파일

- settings.py에서, INSTALLED_APPS에 staticfiles을 추가함 (디폴트)
- 장고는 django.contrib.staticfiles를 제공하여 파일 관리를 돕는다.

settings.py에 

- STATIC_URL 
```python
STATIC_URL = '/static/'
```


클라이언트로부터 페이지에 대한 요청이 왔을 때, 

즉, 템플릿에서 이렇게 요청한 경우 

## STATIC 템플릿 태그

- 템플릿 태그는 정적 파일의 절대 URL을 생성한다. 

```html
{% static 'STATUC URL 이후의 경로' %}
```

예를 들어 
{% static 'img/sample.jpg' %}로, 태그가 있으면, 

runserver는 STATIC_URL + '경로'로 바꾸어 렌더링

-> /static/img/sample.jpg 


## STATICFILES_DIRS

STATICFILES_DIRS = [
 '/var/www/static', 
 os.path.join(BASE_DIR, 'soyeon_pj', 'static')
]

- 특정 앱에 연결되지 않은 static 파일들.  (이라고 하는 데도 있고, 앱/static 등 앱 내의 static 폴더도 등록해야 한다는 문서도 있음..-ㅁ-)
- 개발할 때 STATICFILES_DIR에 등록된 실제 경로에서 해당 정적파일 탐색. 


STATICFILES 
runserver는, settings.py에 등록된 STATIC_URL과 STATICFILES_DIR을 

## STATIC_ROOT 
- 배포 할 때만 사용함. 
- 


## collectstatic
- Files are searched by using the enabled finders. 
- The default is to look in **all locations defined in STATICFILES_DIRS** and **in the 'static' directory of apps specified by the INSTALLED_APPS setting.**


- static root 경로의 폴더 사용.
- Django 프로젝트의 여러 app에서 사용하는 static 파일을 한 곳(프로젝트 폴더의 statics)으로 모아주는 역할을 한다.
(물리적으로 파일을 copy함)

collectstatic을 수행하면, 장고의 앱 안에 있는 모든 static 파일들을 settings.py의 STATIC_ROOT 변수에 지정된 경로로 옮김.


https://crynut84.github.io/2016/11/14/django-static-file/
https://www.opentutorials.org/module/4034/24663
https://cupjoo.tistory.com/116
https://docs.djangoproject.com/ko/3.2/intro/tutorial06/
https://docs.djangoproject.com/en/3.2/ref/contrib/staticfiles/
