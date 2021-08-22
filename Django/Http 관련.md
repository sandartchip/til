
- 장고 runserver에서 너무 아무렇지 않게 해주던 내용들을 찬찬히 정리해보자 =ㅂ=;;


- 장고에는 자체 WAS가 내장되어 있음.

- 그래서 Tomcat 등을 굳이 연동안해도 화면에서 볼 수 있는거임! 하지만 장고 자체 WAS로 배포는 하면 안됨..(보안 이슈 등등)

- WAS(장고 자체 wsgi 웹서버)는 웹 브라우저로부터 (특정 url로 온) 요청을 받으면, 요청올 때 가지고 있던 정보를 HttpRequest객체를 생성하여 저장함.

![image](https://user-images.githubusercontent.com/15938354/130352776-7ea9ebee-017f-4735-b274-200d7f90a174.png)


#### 주요 속성(Attribute)
```
HttpRequest.body      # request의 body 객체
HttpRequest.headers   # request의 headers 객체
HttpRequest.COOKIES   # 모든 쿠키를 담고 있는 딕셔너리 객체 
HttpRequest.method    # request의 메소드 타입 
HttpRequest.GET       #  GET 파라미터를 담고 있는 딕셔너리 같은(?) 객체
HttpRequest.POST      # POST 파라미터를 담고 있는 딕셔너리 같은 객체 
```


- 이걸, 각 컨트롤러에서 매개변수로 받음

![image](https://user-images.githubusercontent.com/15938354/130352999-7db40b21-3cba-40fa-8d9f-013f8e79d493.png)


- 장고의 컨트롤러에서 웹 브라우저에게 응답을 보낼 때 사용하기 위하여 HttpResponse객체를 생성함. (<-맞나..컨트롤러에서 만드는거)

![image](https://user-images.githubusercontent.com/15938354/130353077-d575c685-63eb-4cd9-af93-06810f604df0.png)

- 모든 컨트롤러는 HttpResponse 객체를 리턴해야 함.
(서블릿과의 차이인가..? HttpResponse객체를 서블릿은 WAS가 생성하고, 장고는 컨트롤러에서 만드는게..<-맞나?)

**urls.py
- 서블릿의 RequestMapping(디스패처 서블릿(?))같은 역할을 장고의 urls.py에서 하는게 아닐까?
- 브라우저의 url요청을 컨트롤러와 매핑시켜주는 역할. 


### Request와 Response 객체

- Django의 view (컨트롤러)는 두 가지중 하나를 하도록 되어 있다. 
- 요청된 페이지의 내용이 담긴 HttpResponse 객체를 반환하거나
- 혹은 Http404 같은 예외를 발생하게 해야한다. 


- 아파치 등 사용 안하고 그냥 runserver로 동작 시, 장고 내부의 자체 웹서버가 톰캣 같은 기능을 수행 함. 

- 마치 브라우저에서 서블릿 프로젝트의 url로 요청을 보내면-> 톰캣이, HttpServletRequest라는, 요청의 url, 인코딩 등 정보를 저장하는 객체를 생성하고, 그걸 url mapping에 일치하는 컨트롤러에게 매개변수로 전달하고, 컨트롤러가 해당 리퀘스트를 처리하고 매개변수로 받은 HttpResponse 객체에 다시 클라이언트(브라우저)에 돌려주는 것 처럼. 


- 장고는 request와 response 객체로 서버와 클라이언트가 정보를 주고 받는다. 
- 이를위해 장고는 **django.http 모듈에서 HttpRequest와 HttpResponse API를 제공한다.**


서버-클라이언트 통신 시 아래와 같은 절차로 데이터가 오고 간다.

1) 특정 페이지가 요청(리퀘스트)되면, 장고(의 runserver)는 메타데이터를 포함하는 HttpRequest 객체를 생성한다.
2) 장고는 urls.py에서 정의한 특정 View 클래스/함수에 첫 번째 인자로 해당 객체(request)를 전달한다. 
3) 해당 view는, 결과값을 HttpResponse 혹은 JsonResponse 객체에 담아 전달한다.

### HttpRequest 객체  

예시) 장고에서 리턴한 HttpRequest 객체


#### 사용 사례 
- request.method

```python

if request.method == 'GET'
  do_something()
elif request.method =='POST':
  do_something_else()
  
```

#### 주요 메소드 
```python
HttpRequest.read
HttpRequest.get_host()
HttpReqeust.get_port()
```

### HttpResponse 
예시)

![image](https://user-images.githubusercontent.com/15938354/130352748-773fa2c2-ff86-4784-bba5-57a29756f785.png)


```
HttpResponse(data, content_type)
```
- response를 반환하는 가장 기본적인 함수
- 주로 html을 반환

```
# string 전달하기
HttpResponse("Here is the text of the Web page.")

# html 태그 전달하기 
response = HttpResponse()
>>> response.write("<p>Here's the text of the Web page/</p>")
```

### HttpRedirect 
```
HttpResponseRedirect(url)
```
- 별다른 response를 하지 않고, 지정된 url페이지로 redirect함.
- 첫 번째 인자로 url을 반드시 지정하여야 하며, 절대경로/상대경로를 이용 가능 


### Render

```
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
 
 
```
HttpResponse(data, content_type)

```

- response를 반환하는 가장 기본적인 함수
- 주로 html을 반환

```

# string 전달하기
HttpResponse("Here is the text of the Web page.")


# html 태그 전달하기 

response = HttpResponse()
>>> response.write("<p>Here's the text of the Web page/</p>")

```


### HttpRedirect 


```

HttpResponseRedirect(url)

```

- 별다른 response를 하지 않고, 지정된 url페이지로 redirect함.
- 첫 번째 인자로 url을 반드시 지정하여야 하며, 절대경로/상대경로를 이용 가능 


### Render

```

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
