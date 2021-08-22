- upload는, xml http request 객체의 **프로퍼티**임.


```javascript
    $.ajax({
            type:'POST',
            url: "/upload_file/", // uploadForm은 현재 파일 업로드가 있는 폼 객체. action은 upload file 뷰로 이동.
            enctype: 'multipart/form-data',
            data: input_form_data, // ajax 요청 시 함께 보내는 데이터. html에 바인딩된 파일 객체를 보내야 함.
            beforeSend: function(){

            },
            xhr: function(){
                const xhr = new window.XMLHttpRequest(); //XML HttpRequest 객체를 만든다.

                xhr.upload.addEventListener('progress', e=>{
                    console.log(e);
                });
        
```


- XMLHttpRequest upload 프로퍼티는, 
업로드 진행 상황을 모니터링 할 수 있는 **XMLHttpRequestUpload 객체를 반환**한다. 

- XMLHttpRequestUpload는, start, load, progress, 등의 이벤트 핸들러를 지윈해줘서 업로드 현황에 알맞는 처리를 할 수 있게 해준다.

- upload 이벤트에서 다음 이벤트가 트리거 되어 업로드를 모니터링하는데 사용할 수 있다. 

![image](https://user-images.githubusercontent.com/15938354/115001258-77840080-9ede-11eb-81fe-5fe32167f4e5.png)

