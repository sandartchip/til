

### 이벤트 버블링
- 이벤트 버블링은, 특정 화면 요소에서 이벤트가 발생했을 때 해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성을 의미한다.
- 이벤트가 상위 DOM으로 전파되지 않게 하기 위해서는 event.stopPropagation을 사용해야 한다. 

```html
<body>
  <div class="one">
    <div class="two">
      <div class="three">
      </div>
    </div>
</div>
</body>

const divs = document.querySelectorAll('div');

divs.forEach(function(div){
  div.addEventListener('click', logEvent);
});

function logEvent(event){
  console.log(event.currentTarget.className);
}
```


- div 태그 하나만 클릭했을 뿐인데 3개의 이벤트가 발생되는 이유는 브라우저가 이벤트를 감지하는 방식 때문이다.
- 브라우저는 특정 화면 요소에서 이벤트가 발생했을 때 그 이벤트를 최상위에 있는 화면 요소까지 전파한다.
- event.stopPropagation()은 상위 엘리먼트로의 이벤트 전파를 막는다. 
