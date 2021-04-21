```html
<input type='file' accept='image/jpg,image/png,image/jpeg,image/gif' id='profile_img_upload'/>
<label for='profile_img_upload'><i class="far fa-file-image"/>&nbsp;파일 선택</label>
```

```css
// input file의 기본 모습을 제거
#profile_img_upload{
  width: 0.1px;
	height: 0.1px;
	opacity: 0;
	overflow: hidden;
	position: absolute;
	z-index: -1;
}

#profile_img_upload + label {
    border: 1px solid #d9e1e8;
    background-color: #fff;
    color: #2b90d9;
    border-radius: 2rem;
    padding: 8px 17px 8px 17px;
    font-weight: 500;
    font-size: 15px;
    box-shadow: 1px 2px 3px 0px #f2f2f2;
    outline: none;
}
```

```css
A+B 
```

는, A태그 **바로 다음에 위치하는** B태그를 의미한다.
다른 태그가 A와 B사이에 있으면 적용되지 않는다. 


참고자료: https://gaemi606.tistory.com/entry/%ED%8C%8C%EC%9D%BC-%EC%97%85%EB%A1%9C%EB%93%9C-css%EC%88%98%EC%A0%95%ED%95%98%EA%B8%B0-input-file-custom
