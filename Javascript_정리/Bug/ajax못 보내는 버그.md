

- JSP에서 AJAX로 파라미터를 Insert 컨트롤러에 보낸 이후 다음 화면 전환이 안되는 문제 발생

- 엄청 쫄앗음ㅠ0ㅠ

- 콜백함수에서 ajax 결과가 성공이면 다음 화면 url으로  요청보내는데
- 에러가 뜸
- ajax에러인줄알고 개쫄았는데
- 알고보니 ajax에 보내는 json 객체 값이 잘못됨

```javascript
			option1.numDepth = $("#numDepth").val()인데, 
```

```javascript
			option1.numDepth = $("#numDepth")
```

이라고 함

