### click()과 .on("click")의 차이?

### vanilla js변수 jQuery변수로 만들기
var a;

$(a)를 하면 jQuery 변수가 되고, 

### jQuery의 this와 Javascript의 this

- Javascript의 this는 이벤트가 발생한 element 요소가 표시
- jQuery의 $(this)는 이벤트가 발생한 element의 정보들이 **Object로** 표시된다. 
- (내가 생각한 것처럼, DOM 객체 자체가 바인딩되는게 아님.)

- $(this).val()은, oject 형태로 받아온 this의 **value** 값을 가져오는것. 
(따라서 this가 a 객체이면, val()값이 없다.)


#### div에서 이벤트가 발생했을 때, this와 $(this)를 출력했을 때 나타나는 정보
![image](https://user-images.githubusercontent.com/15938354/117978001-59d67980-b36c-11eb-83b6-8271551f6e91.png)

즉, Javascript의 this == jQuery의 $(this)[0]

이미지 출처:https://haenny.tistory.com/84#:~:text=%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20this%EC%99%80%20%EC%A0%9C%EC%9D%B4%EC%BF%BC%EB%A6%AC%20%24(this)%EB%8A%94%20%EB%AA%85%EC%B9%AD,%EB%90%98%EB%8A%94%20%EC%A0%95%EB%B3%B4%EB%8A%94%20%EC%84%9C%EB%A1%9C%20%EB%8B%A4%EB%A5%B4%EB%8B%A4.&text=%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%9D%98%20this%20%EA%B2%BD%EC%9A%B0,%EB%93%A4%EC%9D%B4%20Object%EB%A1%9C%20%ED%91%9C%EC%8B%9C%EB%90%9C%EB%8B%A4.



### 제이쿼리 변수

#### var a와 var $a의 차이점?
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
### next()
선택한 요소의 바로 다음에 위치한 형제 요소.


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
