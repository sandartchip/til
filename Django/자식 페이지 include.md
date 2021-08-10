
## include 
```
{% include "서브 페이지.html" %}
```


```python

# views.py 

def index(request):
  template = loader.get_template('index.html')
  context = {'text':하이룽'}
  
  return HttpResponse
  
```

```html

<!DOCTYPE html>
# index.html

<html>
  <head></head>
  <body>
    <h2>테스트</h2>
    {% include "hi.html" %}
  </body>
</html>

```

```html
# hi.html
<h1>{{ text }}</h1>
```

부모 페이지에서 포함시킨 자식 템플릿에도, **부모 템플릿을 렌더링 한 뷰(컨트롤러)에서 전달한 컨텍스트의 적용 대상이 된다.**

부모니 자식이니 뭐니 해도 그냥 그 영역에 html만 오버라이딩 한 것 일 뿐이기 때문..

부모 템플릿의 context가 그대로 자식 template에 전달 (context는 변수 목록)

자식 페이지 렌더링 시, 뷰에서 렌더링 시킨 변수는 서브 페이지에도 렌더링 된다. 

![image](https://user-images.githubusercontent.com/15938354/128476245-b8c79fa2-8e4c-4657-b94a-12bd6212bd75.png)
