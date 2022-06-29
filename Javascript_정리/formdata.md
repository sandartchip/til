
# FormData

- FormData objects can help with that. As you might have guessed, it’s the object to represent HTML form data.
- (FormData는, HTML formdata를 표현하기 위한 객체이다.)

The constructor is:
```javascript
 let formData = new FormData([form]);
```

If HTML form element is provided, it automatically captures its fields.

The special thing about FormData is that network methods, such as fetch, can accept a FormData object as a body. 

From the server point of view, that looks like a usual form submission.



- FormData 인터페이스는 양식 필드와 해당 값을 나타내는 키/값 쌍 집합을 쉽게 구성할 수 있는 방법을 제공

- 이 값은 fetch() 또는 XMLHttpRequest.send() 메서드를 사용하여 쉽게 전송할 수 있다. 
 
- 인코딩 유형이 "multipart/form-data"로 설정된 경우 폼이 사용하는 것과 동일한 형식을 사용함.



