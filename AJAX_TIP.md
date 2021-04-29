

### Question

한 페이지에서 ajax 여러개를 호출할 때,

1번 ajax 로딩 후 2번 ajax가 처리되어야 하는데

2번 ajax가 서버에서 먼저 처리되는 문제가 있다.


### ANSWER

jQuery ajax 옵션 중 async가 있다.

ajax여러 개 실행 시 순서대로 하게 하려면, 

```javascript 
$.ajax({ 
  ...
  async:false,
  ...
  });
```
옵션을 줘야 한다. 

해당 옵션을 주면, 1번 ajax 처리가 끝나 response 데이터를 받은 후 2번 ajax를 순차적으로 실행하게 된다.
