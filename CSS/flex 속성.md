

#### flex 속성
- 요소들을 자유자재로 위치시킨다. 
- 부모 요소(div.container)를 flex container라고 부르고,
- 자식 요소인 div.item을 flex item(플렉스 아이템)이라고 부른다.
- flex 컨테이너에 disply: flex를 적용하는게 시작이다.

```css
.container {
	display: flex;
	/* display: inline-flex; */
}
```

![image](https://user-images.githubusercontent.com/15938354/158519322-0defd8c2-b501-4329-9602-892a850db32d.png)

- flex 아이템들은 가로로 배치되고, 자신이 가진 내용물의 width만큼 차지하게 된다. 마치 inlihe 요소 처럼.
