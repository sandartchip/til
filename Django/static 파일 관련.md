
## url 에서 요청

- 아파치, nginx 등에 deploy하지 않은 개발 환경에서는
- settings.py에 STATIC_ROOT로 collectstatic 경로 지정해주고,
- (앱의) urls.py에
 
```python
settings.py

STATIC_ROOT = os.path.join(BASE_DIR, 'collected_statics')
```

```
디렉토리 구조

collected_statics 
 ㄴ static
      ㄴ 앱 명
          ㄴ css
          ㄴ js
          ㄴ image
```


```python
urlpatterns += static(settings.STATIC_URL, document_root = settings.STATIC_ROOT)
```
추가하면, ```url:포트/(앱의 url에 등록한 경우, 앱 명)/static/앱 명/js/....``` 으로 static 파일들 사용 가능 .

# Djangos와 static파일

- settings.py에서, INSTALLED_APPS에 staticfiles을 추가함 (디폴트)
- 장고는 **django.contrib.staticfiles**를 제공하여 파일 관리를 돕는다.

## STATIC 템플릿 태그

- {% static %} 템플릿 태그는, **정적 파일의 절대 URL을 생성한다.**

예시) 
```html
{% static 'STATUC URL 이후의 경로' %}
```

예를 들어 ```STATIC_URL = '/static/'``` 이고

```{% static 'img/sample.jpg' %}```로, 태그가 있으면, 

runserver는 해당 템플릿 태그를 ```/static/img/sample.jpg``` (STATIC_URL + '경로')로 바꾸어 렌더링





#### 템플릿 태그 사용법

1. settings.py에서 INSTALLED_APPS에   django.contrib.staticfiles 가 추가된 걸 확인함

2. settings.py에서 static url을 다음과 같이 세팅

- STATIC_URL 
```python
STATIC_URL = '/static/'
```


3. 클라이언트에서 HTML 요청

클라이언트로부터 페이지에 대한 요청이 왔을 때, 즉, 템플릿에서 이렇게 요청한 경우 

```html
{% load static %}
<img src="{% static 'my_app/example.jpg' %}" alt="My image">
```

4. 앱 디렉토리 하위 static 폴더 안에, 정적 파일 저장 
ex) my_app/static/my_app/example.jpg.

myapp모듈에서 사용할 Static파일들을 저장하는 디렉토리는 myapp/static/**myapp** 이다. 

- (귀찮다고 해서) myapp/static 디렉토리에 바로 static 파일들을 위치시키면, 
- 여러 개 앱에 같은 이름의 static파일(예시: myapp/static/style.css, myapp2/static/style.css) 이 있을 때 
1. 템플릿에서 {% static 'style.css' %} 으로 했을 때, 어느 앱인지 알 수가 없다. 
2. collectstatic으로 통합 static 디렉토리 생성할 때 이름이 중복이므로, 충돌. 


- 결국, static 파일 위치는 static 밑에 폴더 하나 더 만들어서...myapp/static/**myapp**/mypage.css

 
- Django에서는 Static 파일들을 모듈별 Local영역과 Global영역 두 단계로 나누어서 관리를 한다. 


- Local영역에는 각 모듈에서 독자적으로 사용되는 Static파일들이 위치한다. (기본적으로 앱 아래에 있는 static 폴더를 탐색한다.)

추가적인 경로를 탐색하게 하려면 Global 영역의 리스트를 추가해야한다.
- Global영역(STATICFILES_DIRS)에는 사이트 전역에서 공통적으로 사용하는 Static파일들이 위치한다.



## STATICFILES_DIRS

STATICFILES_DIRS = [
 '/var/www/static', 
 os.path.join(BASE_DIR, 'soyeon_pj', 'static')
]

- 특정 앱에 연결되지 않은 static 파일들.  (이라고 하는 데도 있고, 앱/static 등 앱 내의 static 폴더도 등록해야 한다는 문서도 있음..-ㅁ-??)
- 개발할 때 STATICFILES_DIR에 등록된 실제 경로에서 해당 정적파일 탐색. 

햇갈려서 공식문서를 찾아봄.

- 아무 생각 없이 추가 한 django.staticfiles.finders에 FileSystemFinder와 AppDirectoriesFinder가 있는데, 이 객체들이 참조 할 static 폴더 경로를 찾는다. 
 
## 공식문서
#### STATICFILES_DIR
- The list of finder backends that know **how to find static files in various locations.**

- The default will find files **stored in the STATICFILES_DIRS setting** (using django.contrib.staticfiles.finders.FileSystemFinder) and in a **static subdirectory of each app (using django.contrib.staticfiles.finders.AppDirectoriesFinder).**
 
- If multiple files with the same name are present, the first file that is found will be used. 

- One finder is disabled by default: django.contrib.staticfiles.finders.DefaultStorageFinder. 

- If added to your STATICFILES_FINDERS setting, it will look for static files in the default file storage as defined by the DEFAULT_FILE_STORAGE setting.

그러니까 STATIC_URL이 /static/이고
{% static 'js/test/' %} 라는 태그가 html에 있으면

장고, static finder의 finder는 appdirectory finder는 앱 디렉토리/static/..을 찾아보고 STATICFILES_DIRS에 선언된 디렉토리들/static도  찾음

STATICFILES 
runserver는, settings.py에 등록된 STATIC_URL과 STATICFILES_DIR을 

## 배포와 STATIC ROOT 
https://docs.djangoproject.com/en/3.2/howto/static-files/deployment/

## STATIC_ROOT 
- 배포 할 때만 사용함. 


## collectstatic

- Django 프로젝트의 여러 app에서 사용하는 static 파일을 한 곳(프로젝트 폴더의 statics)으로 모아주는 역할을 한다.

**어디서?**
- STATICFILES_DIR에 명시된 경로에 있는 모든 정적 파일들과, INSTALLED_APPS 목록에 등록된 앱이 사용하는 모든 정적파일들(static 디렉토리의 파일)


**어디로?**
- static root 경로의 폴더에 물리적으로 파일을 copy함

collectstatic을 수행하면, 장고의 앱 안에 있는 모든 static 파일들을 settings.py의 STATIC_ROOT 변수에 지정된 경로로 옮김.

https://www.tuwlab.com/ece/26424
https://crynut84.github.io/2016/11/14/django-static-file/
https://www.opentutorials.org/module/4034/24663
https://cupjoo.tistory.com/116
https://docs.djangoproject.com/ko/3.2/intro/tutorial06/
https://docs.djangoproject.com/en/3.2/ref/contrib/staticfiles/
