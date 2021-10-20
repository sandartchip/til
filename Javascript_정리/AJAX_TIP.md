
### 부분리로드

```javascript
     $("#file_list").load(location.href + " #input_file_table");

```
### $.load() 하기 전
![image](https://user-images.githubusercontent.com/15938354/138017786-ea6eca40-5b2a-48ad-ae44-32016f1ee7f3.png)


### $.load() 한 후 
![image](https://user-images.githubusercontent.com/15938354/138017719-7af25c4b-285c-4776-9cd7-b17a6bde0c7f.png)

이렇게 부분 리로드를 하고 나면, GET방식으로 해당 페이지 재요청함 

- AJAX 부분 리로드라서 GET 방식 리로드 안 될 줄 알았는데 다시 함 -ㅁ-;;;
 
### Question

한 페이지에서 ajax 여러개를 호출할 때,

1번 ajax 로딩 후 2번 ajax가 처리되어야 하는데

2번 ajax가 서버에서 먼저 처리되는 문제가 있다.


### ANSWER

jQuery ajax의 기본 옵션은 비동기다. 
즉, aJax로 요청한 데이터의 응답을 기다리지 않고 바로 다음 작업을 실행하게 된다. 

그러면 ajax로 서버 측에 데이터 요청 후, 요청의 결과를 모두 수신받은 상태에서 다음 작업을 하는 동기식 방식을 실행하려면 어떻게 해야 할까? 

ajax여러 개 실행 시 순서대로 하게 하려면, 

```javascript 
$.ajax({ 
  ...
  async:false,
  ...
  });
```
옵션을 줘야 한다. 


jQuery의 Ajax 호출은 async: true(비동기 설정)가 기본이다.
따라서, **async: false**  속성을 기입하지 않는다면 기본적으로 비동기식으로 작동하게 된다.
즉, Ajax 호출 후 응답을 받았는지 확신할 수가 없다. 

해당 옵션을 주면, 1번 ajax 처리가 끝나 **response 데이터를 받은 후** 2번 ajax를 순차적으로 실행하게 된다.


https://recollectionis.tistory.com/167
