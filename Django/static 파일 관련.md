

# Djangos와 static파일

- settings.py에서, INSTALLED_APPS에 staticfiles을 추가함 (디폴트)
- 장고는 django.contrib.staticfiles를 제공하여 파일 관리를 돕는다.

## STATIC 템플릿 태그

- 템플릿 태그는 정적 파일의 절대 URL을 생성한다. 


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

- myapp/static 디렉토리에 바로 static 파일들을 위치시키면, 
- 여러 개 앱에 같은 이름의 static파일(예시: myapp/static/style.css, myapp2/static/style.css) 이 있을 때 
1. 템플릿에서 {% static 'style.css' %} 으로 했을 때, 어느 앱인지 알 수가 없다. 
2. collectstatic으로 통합 static 디렉토리 생성할 때 이름이 중복이므로, 충돌. 


귀찮다고 해서 그냥 myapp/static디렉토리에 바로 myapp에서 사용할 Static파일들을 위치시키면, 다른 모듈에 같은 이름의 Static파일이 존재하는 경우 요청에 대해 잘못된 Static파일이 전달되는 충돌이 발생할 수 있습니다. 또한, 운영 서버에서 collectstatic명령으로 통합 static디렉토리를 생성할 때 어느 한쪽 파일이 다른 파일에 의해 덮어씌워져 누락되는 문제가 발생합니다.

이제 myapp/static/myapp/mypage.css파일을 다음과 같이 작성합니다. 간단한 예제로, 본문의 글자 색을 모두 파란색으로 바꿔 보도록 하겠습니다. (여기서는 예시를 위해 myapp디렉토리에 바로 CSS파일을 위치시켰지만, 실제 프로젝트에서는 css, js, image등과 같이 Static파일의 종류별 하위 디렉토리를 따로 구성하는 것이 좋습니다.)

 

```html
{% static 'STATUC URL 이후의 경로' %}
```

예를 들어 
{% static 'img/sample.jpg' %}로, 태그가 있으면, 

runserver는 STATIC_URL + '경로'로 바꾸어 렌더링

-> /static/img/sample.jpg 



- Django에서는 Static 파일들을 모듈별 Local영역과 Global영역 두 단계로 나누어서 관리를 한다. 


- Local영역에는 각 모듈에서 독자적으로 사용되는 Static파일들이 위치한다. (기본적으로 앱 아래에 있는 static 폴더를 탐색한다.)

추가적인 경로를 탐색하게 하려면 Global 영역의 리스트를 추가해야한다.
- Global영역(STATICFILES_DIRS)에는 사이트 전역에서 공통적으로 사용하는 Static파일들이 위치한다.



## STATICFILES_DIRS

STATICFILES_DIRS = [
 '/var/www/static', 
 os.path.join(BASE_DIR, 'soyeon_pj', 'static')
]

- 특정 앱에 연결되지 않은 static 파일들.  (이라고 하는 데도 있고, 앱/static 등 앱 내의 static 폴더도 등록해야 한다는 문서도 있음..-ㅁ-)
- 개발할 때 STATICFILES_DIR에 등록된 실제 경로에서 해당 정적파일 탐색. 


STATICFILES 
runserver는, settings.py에 등록된 STATIC_URL과 STATICFILES_DIR을 

## 배포와 STATIC ROOT 
https://docs.djangoproject.com/en/3.2/howto/static-files/deployment/

## STATIC_ROOT 
- 배포 할 때만 사용함. 


## collectstatic

- Django 프로젝트의 여러 app에서 사용하는 static 파일을 한 곳(프로젝트 폴더의 statics)으로 모아주는 역할을 한다.

**어디서?**
- STATICFILES_DIR에 있는 파일과, INSTALLED_APPS의 static 디렉토리의 파일을 찾아서

**어디로?**
- static root 경로의 폴더에 물리적으로 파일을 copy함

collectstatic을 수행하면, 장고의 앱 안에 있는 모든 static 파일들을 settings.py의 STATIC_ROOT 변수에 지정된 경로로 옮김.

https://www.tuwlab.com/ece/26424
https://crynut84.github.io/2016/11/14/django-static-file/
https://www.opentutorials.org/module/4034/24663
https://cupjoo.tistory.com/116
https://docs.djangoproject.com/ko/3.2/intro/tutorial06/
https://docs.djangoproject.com/en/3.2/ref/contrib/staticfiles/
