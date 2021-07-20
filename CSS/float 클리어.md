
```html

<div class="float_ex">
  <div class="left">좌측</div>
  <div class="right">우측</div>
</div>
```

```css
#float_ex:after {content:""; display:block; clear:both;}  /* 표준계열 브라우저에 대응하는 float 해제용 가상 엘리먼트의 생성 */
#float_ex {*zoom:1;} /* IE5.5~7 브라우저 대응 Hack */
```


참고로, 부모 태그 안에 같이 묶인 **모든 요소**에는 float 속성이 **모두 들어가 있어야 합니다.**

마지막 div 태그만 위 태그의 오른쪽으로 보내고 싶다고 해서 마지막 div 태그에만 css float 속성을 부여할 수 없다는 것입니다.

-> 부모 요소 안의 자식 요소 몇 개만 float 시킬 수 있는 줄 알았다..
