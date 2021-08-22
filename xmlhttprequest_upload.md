- upload는, xml http request 객체의 **프로퍼티**임.


```javascript

xhr: function(){
        const xhr = new window.XMLHttpRequest();
        
        xhr.upload.addEventListener('progress', e=>{
            console.log(e);
        });
        
```


- XMLHttpRequest upload 프로퍼티는, 
업로드 진행 상황을 모니터링 할 수 있는 **XMLHttpRequestUpload 객체를 반환**한다. 

- XMLHttpRequestUpload는, start, load, progress, 등의 이벤트 핸들러를 지윈해줘서 업로드 현황에 알맞는 처리를 할 수 있게 해준다.

- upload 이벤트에서 다음 이벤트가 트리거 되어 업로드를 모니터링하는데 사용할 수 있다. 

![image](https://user-images.githubusercontent.com/15938354/115001258-77840080-9ede-11eb-81fe-5fe32167f4e5.png)

