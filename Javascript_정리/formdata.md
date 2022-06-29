
# FormData

- FormData objects can help with that. As you might have guessed, it’s the object to represent HTML form data.
- FormData는, HTML formdata를 표현하기 위한 객체이다.
- Formdata는, 폼을 쉽게 보내도록 도와주는 객체이다.
- The FormData interface provides a way to easily construct a set of key/value pairs representing form fields and their values, 
which can then be easily sent using the fetch() or XMLHttpRequest.send() method. 
- It uses the same format a form would use if the encoding type were set to "multipart/form-data".

The constructor is:
```javascript
 let formData = new FormData([form]);
```

- HTML에 form 요소가 있는 경우, 위와 같은 코드를 작성하면 해당 폼 요소의 필드 전체가 자동 반영됨.
- fetch 등의 네트워크 메서드가 FormData 객체를 바디로 받는다는 건 FormData의 특징입니다. 이때 브라우저가 보내는 HTTP 메시지는 인코딩되고 Content-Type 속성은 multipart/form-data로 지정된 후 전송됩니다.

서버 관점에선 FormData를 사용한 방식과 일반 폼 전송 방식에 차이가 없습니다.

```html
<form id="formElem">
  <input type="text" name="name" value="Bora">
  <input type="text" name="surname" value="Lee">
  <input type="submit">
</form>

<script>
  formElem.onsubmit = async (e) => {
    e.preventDefault();

    let response = await fetch('/article/formdata/post/user', {
      method: 'POST',
      body: new FormData(formElem)
    });

    let result = await response.json();

    alert(result.message);
  };
</script>
```


- FormData 인터페이스는 양식 필드와 해당 값을 나타내는 키/값 쌍 집합을 쉽게 구성할 수 있는 방법을 제공

- 이 값은 fetch() 또는 XMLHttpRequest.send() 메서드를 사용하여 쉽게 전송할 수 있다. 
 
- 인코딩 유형이 "multipart/form-data"로 설정된 경우 폼이 사용하는 것과 동일한 형식을 사용함.

https://ko.javascript.info/formdata

