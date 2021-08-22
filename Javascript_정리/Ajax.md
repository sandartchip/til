
- **브라우저**는 **XMLHttpRequest 객체를 사용해서** Ajax 요청을 생성한다. 
- 서버가 브라우저의 요청에 대해 응답을 반환하면, 같은 XMLHttpRequest 객체가 그 결과를 처리한다.

```javascript
$.ajax(
    "url" : "URL 경로 : www.naver.com",
    "data" : {
        "param1" : "param1",
        "param2" : 12
    },
    "dataType" : "json",
    "type" : "post",
    "beforeSend" : function() {
        if(검증 실패시) {
             return false;
        }      
        return true;
    },
    "success" : function(data) {
        alert("썩쎄쓰!");
    },
    "error" : function() {
        alert("에러났소!");
    }
);
```

|속성|설명|
|---|---|
|url| 말그대로 url |
|xhr| ajax object(xhr)를 커스텀해서 세팅할 때 사용한다. |
|data|서버로 전달될 데이터 |
|dataType| 서버로부터 반환될 데이터의 type. (xml, json, jsonp, script, html)|
|type|form의 method 속성(GET/POST)|
|beforeSerialize|폼이 조립되기 전에 호출되는 함수. 폼에 값을 강제로 넣거나 변경해야 할 필요성이 있을 경우, 이 위치에서 작업을 처리해야한다|
|beforeSend|AJAX가 호출되기 전 호출되는 콜백 매서드 설정. 여러가지 반환 타입을 제공하지만, 예제 정도만 해도 충분한듯.|
|success|서버와의 통신이 잘 이루어졌을 때 호출되는 이벤트 핸들러|
|error| 서버상에서 문제가 발생할 경우 호출되는 이벤트 핸들러|
|async|요청 시 동기화 여부 (default: true, 비동기)
|xhr| ajax object(xhr)를 커스텀해서 세팅할 때 사용한다. |


https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=shadowbug&logNo=220650479226
