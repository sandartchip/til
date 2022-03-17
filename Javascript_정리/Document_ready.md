
- 문서 객체 모델(DOM) 이 모두 로딩되었을 때.
- js와같은경우 dom element가 로딩되기 전에,  즉 **body전 부분에** 스크립트를 작성하면 js가 동작하지않는다.
- 하지만 저렇게 jquery를 선언해주면, dom을 모두 로딩한 후 해당 함수를 실행하기때문에 body상단에 작성을 해줘도 js가 잘돌아간다.
- jquery의 Document.ready와 기본 js의 DOMContentLoaded는 같음.

