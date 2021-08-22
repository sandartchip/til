


## HttpResponse

html파일, 이미지 등 다양한 응답을 해줄 수 있다. 

하나의 함수는 **최소 하나의 HttpResponse를 반환해야 한다.**

이는 views에서 검사하는게 아니라 middleware에서 검사하게 된다. 

```python
# config/settings.py

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

middleware는 다음과 같이 app을 감싸고 있으면서, request가 들어올 때는 적절하게 가공해주고, response가 나갈 때도 확인을 해 준다.   

![image](https://user-images.githubusercontent.com/15938354/114992179-6c78a280-9ed5-11eb-8f48-bbb15a296aed.png)  





### HttpResponse 
예시) index.html을 렌더하는 컨트롤러의 Response 객체

![image](https://user-images.githubusercontent.com/15938354/130352748-773fa2c2-ff86-4784-bba5-57a29756f785.png)


```python
HttpResponse(data, content_type)
```
- response를 반환하는 가장 기본적인 함수
- 주로 html을 반환

```python
# string 전달하기
HttpResponse("Here is the text of the Web page.")

# html 태그 전달하기 
response = HttpResponse()
>>> response.write("<p>Here's the text of the Web page/</p>")
```

### HttpRedirect 
```python
HttpResponseRedirect(url)
```
- 별다른 response를 하지 않고, 지정된 url페이지로 redirect함.
- 첫 번째 인자로 url을 반드시 지정하여야 하며, 절대경로/상대경로를 이용 가능 


### Render

```python
render(request(필수), template_name(필수), context=None, content_type=None, status=None, using=None)
```
- template 에 context 를 채워넣어 표현한 결과를 HttpResponse 객체와 함께 돌려준다. 

```python

views.py 

def index(request):
    template = loader.get_template('index.html')
    context = {'text': '하이룽'}
    
    return HttpResponse(template.render(context, request))
```

- 자주 쓰는 용법이다. 따라서 Django 는 이런 표현을 쉽게 표현할 수 있도록 단축 기능(shortcuts)을 제공합니다. index() view 를 단축 기능으로 작성하면 다음과 같습니다.

- render는 **HttpResponse 객체를 반환**하는 함수.
- **template을 context와 엮어 HttpResponse로 쉽게 반환**해준다.
- 복잡한 화면이 렌더링 되니 기본적인 Http Response와 뭔가 다른가 싶겠지만, 본질은 같은 것이다. Http 요청에 대한 응답을 리턴하는 것이다. 

- context에는, View에서 사용하던 변수(dictionary 자료형)을 html 템플릿에 전달. 
- 인수인 context로 표현 된 템플릿의 Http Response 객체가 반환된다. 
- key값이 템플릿에서 사용할 변수 이름, value값이 파이썬 변수가 된다.


###  JsonReponse 
```
JsonReponse(data, encoder=DjagnoJSONEncoder, safe=True, json_dumps_params=None, **kwargs)

```

- HttpResponse의 subclass
- JSON-encoded response를 생성할 수 있게 해 줌.
- 첫 번째 인자는 전달한 데이터로, 반드시 dictionary 객체여야 함.
- 기본 Content-type 헤더는 application/json임.
- encoder는 데이터를 serialize할 때 사용됨. (->??)
ython


```python
HttpRequest.read
HttpRequest.get_host()
HttpReqeust.get_port()
``` 

### HttpResponse 
 
 
```python
HttpResponse(data, content_type)

```

- response를 반환하는 가장 기본적인 함수
- 주로 html을 반환

```python

# string 전달하기
HttpResponse("Here is the text of the Web page.")


# html 태그 전달하기 

response = HttpResponse()
>>> response.write("<p>Here's the text of the Web page/</p>")

```


### HttpRedirect 


```python

HttpResponseRedirect(url)

```

- 별다른 response를 하지 않고, 지정된 url페이지로 redirect함.
- 첫 번째 인자로 url을 반드시 지정하여야 하며, 절대경로/상대경로를 이용 가능 


### Render

```python

render(request(필수), template_name(필수), context=None, content_type=None, status=None, using=None)

```

- render는 **HttpResponse 객체를 반환**하는 함수.
- **template을 context와 엮어 HttpResponse로 쉽게 반환**해준다.
- context에는, View에서 사용하던 변수(dictionary 자료형)을 html 템플릿에 전달. 
- key값이 템플릿에서 사용할 변수 이름, value값이 파이썬 변수가 된다.




###  JsonReponse 

```
JsonReponse(data, encoder=DjagnoJSONEncoder, safe=True, json_dumps_params=None, **kwargs)

```

- HttpResponse의 subclass
- JSON-encoded response를 생성할 수 있게 해 줌.
- 첫 번째 인자는 전달한 데이터로, 반드시 dictionary 객체여야 함.
- 기본 Content-type 헤더는 application/json임.
- encoder는 데이터를 serialize할 때 사용됨. (->??)
- JsonResponse는 response를 커스터마이징하여 전달하고 싶을 때, HTTP Staus code에 더하여 메세지를 입력하여 전달 가능하다.
- 딱히 전달할 메세지가 없고, status code만 전달하는 경우에는 HttpResponse를 사용하면 된다. 


참고:https://velog.io/@jcinsh/Django-request-response
참고:https://ssungkang.tistory.com/entry/Django-HttpRequest-HttpResponse
