
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
