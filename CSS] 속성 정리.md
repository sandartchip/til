
### opacity 0 

```css

opacity: 0 

```

투명도가 0으로 설정된다. 
투명도는 그림에만 적용되는 속성으로 생각하기 쉽지만, 
텍스트에도 적용된다. opacity:0을 적용하면, 영역 자체가 사라지는 display:block과 달리 영역이 있다. 또한, 해당 영역에 대해 이벤트(예시: click)가 작동한다.


### width 속성

width의 % 요소 : 부모 요소에 **상대적인** 너비.  


### nth-child 속성 
=> 부모 안의 **모든 요소** 중 N번째 요소. 

```html

<div id="test">
  <p>Ttitle</p>
  <ul>
  </ul>
  <ul>
  </ul>
```

```css
  div#test ul:nth-child(1){ 
    
   }
  div#test ul:nth-child(2) {
  
   }
```

이렇게 css 줄 경우에, nth-child(2)는 첫 번째 ul에 걸린다. 
나는 nth-child 속성이 태그명까지 구분한다 생각했지만 아님. 

### nth-of-type

내가 생각한 방식대로 스타일이 적용되게 하려면 nth-of-type을 적용해야 한다.

즉, 부모 안의 요소 중 1번재 ul요소, 2번째 ul 요소에 적용된다.

