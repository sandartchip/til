## XMLHttpRequest

XMLHttpRequest(XHR) 객체는 서버와 상호작용하기 위하여 사용된다.

전체 페이지의 새로고침없이도 URL 로부터 데이터를 받아올 수 있다. 

이는 웹 페이지가, 사용자가 하고 있는 것을 방해하지 않으면서 페이지의 일부를 업데이트할 수 있도록 해 준다. 

XMLHttpRequest 는 AJAX 프로그래밍에 주로 사용된다.



XMLHttpRequest 는 이름으로만 봐서는 XML 만 받아올 수 있을 것 같아 보이지만, 
모든 종류의 데이터를 받아오는데 사용할 수 있다. 

또한 HTTP 이외의 프로토콜도 지원한다(file 과 ftp 포함).


브라우저는 XMLHttpRequest 객체를 이용하여 Ajax 요청을 생성하고 전송한다. 

서버가 브라우저의 요청에 대해 응답을 반환하면, 같은 XMLHttpRequest 객체가 그 결과를 처리한다.


```
// XMLHttpRequest 객체의 생성
const xhr = new XMLHttpRequest();

// 비동기 방식으로 Request를 오픈한다
xhr.open('GET', '/users');

// Request를 전송한다
xhr.send();
```



### 생성자
```
XMLHttpRequest() 
```

생성자는 XMLHttpRequest 를 초기화한다. 

다른 모든 메소드 호출이전에 호출되어야 한다.


참고 자료:
https://developer.mozilla.org/ko/docs/Web/API/XMLHttpRequest

