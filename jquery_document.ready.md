
```
$(document).ready(function() { 
  // DOM이 로드되었을 때 실행되어야 하는 코드 
  });
```

jQuery에서 document 객체의 ready 이벤트. 

문서 객체모델( Document Object Model)이 모두 로딩되었을 때 $(document).ready() 한에 위치한 코드가 실행 된다. 

$(document).ready() 는, 해당 구문의 안에 있는 코드가 실행되기 전에, **페이지를 구성하는 DOM 객체를 로딩하는걸 보장**해준다. 

따라서, DOM 객체를 다루는 코드를 사용한다면 
반드시 이 구문 안에 해당 코드를 위치시켜야 제대로 작동함을 보장한다.

참고:https://twinsoul.tistory.com/74
