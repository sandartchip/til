
```
$(document).ready(function() { 
  // DOM이 로드되었을 때 실행되어야 하는 코드 
  });
```

jQuery에서 document 객체의 ready 이벤트. 

문서 객체모델( Document Object Model ) 즉 HTML 소스가 전부 로딩되었을 때 $(document).ready() 한에 위치한 코드가 실행 된다. 

$(document).ready() 는, 해당 구문의 안에 있는 코드가 실행되기 전에, **페이지를 구성하는 DOM 객체를 로딩하는걸 보장**해준다. 

따라서, DOM 객체를 다루는 코드를 사용한다면 
반드시 이 구문 안에 해당 코드를 위치시켜야 제대로 작동함을 보장한다.


**Q. 그러면 모든 DOM element에 대한 함수를 document.ready 안에 적어야 하나?**

A. 이벤트 같은 경우에는, 문서가 전부 로드 될 때 까지 기다릴 필요가 없음.(->확인 요망)

참고:https://twinsoul.tistory.com/74
