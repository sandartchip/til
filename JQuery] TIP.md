
### 제이쿼리 변수

- var a와 var $a의 차이점?
- var a
 자바스크립트 변수. 스크립트만 사용 가능.
- var $a
  jQuery 변수. jQuery에서 사용하는 내장 함수 전부 사용 가능. 
  
- 예시
```javascript
var a;
a.css('backgroundcolor', 'blue')-> 메소드가 안 먹음.

var $a;
$a.css('backgroundcolor', 'blue')-> a는 제이쿼리 변수이므로, 해당 css속성이 반영.
```

### val()
.val()

요소의 value를 가져옴.

ex)

```html

<input type="hidden" id="test_id" class="test_class" name="test_name" value="test">

```

```javascript 

var value_by_id = $('#test_id').val();

var value_by_class = $('.test_class').val();

var value_by_name = $('input[name=test_name]').val();

```
