

###  $(function(){ } );

- ```$(document).ready( function() {}; );``` 와 ``` $(function(){ };```는 동일한 의미이다.

```
<!DOCTYPE html>
<html>
<head>
<script src="jquery.js"></script>
<script>
$(document).ready(function(){

... jQuery 메소드, 액션을 입력 ...

});
</script>
```

```
<script>

$(function(){
... jQuery 메서드, 액션을 입력 ...
});
</script>
```

### click()과 .on("click")의 차이?

- click() 이벤트는 최초에 페이지를 로딩할 때 선언되어 있던 element에 이벤트를 바인딩하고 나서 더 이상 동적 바인딩 X. 
 
- on("click") 이벤트는, 부모의 이벤트를 자식 태그에 delegate시킴. 
 
- 동적으로 추가된 태그에게 이벤트를 바인딩 시킬 수 있다. 




### vanilla js변수 jQuery변수로 만들기
var a;

$(a)를 하면 jQuery 변수가 된다.



### jQuery의 this와 Javascript의 this

- Javascript의 this는 이벤트 핸들러가 등록된 DOM 요소를 가리킨다. 
- jQuery 함수를 사용하려면, $(this)와 같이 감싸서 jQuery 객체로 만들어야 한다.

```javascript 

$("#some").on("click", function(e) {
   this;     //<= jQuery로 감싸지 않은 요소 (예: <div id="some">..</div>
   $(this);  // <= jQuery로 감싼 요소 
}

```

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


#참고자료

https://lookingfor.tistory.com/entry/JQuery-%ED%81%B4%EB%A6%AD-%EC%9D%B4%EB%B2%A4%ED%8A%B8-onclick-%EA%B3%BC-click-%EC%9D%98-%EC%B0%A8%EC%9D%B4
https://d2.naver.com/helloworld/1855209
