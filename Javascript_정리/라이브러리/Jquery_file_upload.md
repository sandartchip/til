### AJAX Options

The jQuery File Upload plugin makes use of jQuery.ajax() for the file upload requests. 
(jQuery file upload plugin은, 파일 업로드 요청이 있을 때, jQuery.ajax()를 사용하게 만든다.) 

This is true even for browsers without support for XHR, thanks to the Iframe Transport plugin.

The options set for the File Upload plugin are passed to jQuery.ajax() and allow to define any ajax settings or callbacks.
- 파일 업로드 플러그인 옵션은, jQuery.ajax()로 전달된다. 

The ajax options processData, contentType and cache are set to false for the file uploads to work and should not be changed.



### 기본 플러그인 
https://github.com/blueimp/jQuery-File-Upload/wiki/Basic-plugin


### API 설명
(https://github.com/blueimp/jQuery-File-Upload/wiki/API)

### Adding additional form data programmatically

```javascript 
$('#fileupload').fileupload({
    formData: {example: 'test'}
});
```

cf)  formData는 본래, form field의 key와 value를 쉽게 구성하는 인터페이스를 제공한다. 

- 위의 formData는 html에 inline방식으로 쓰일 수 있음.
 
### Data attributes

It is possible to pass options to the initialization method as HTML5 data attributes:

```html

<input id="fileupload" type="file" name="files[]" multiple
    data-url="/path/to/upload/handler.json"
    data-sequential-uploads="true"
    data-form-data='{"script": "true"}'>

```

```javascript
/* Initializes the File Upload widget with*/

{
    url: '/path/to/upload/handler.json',
    sequentialUploads: true,
    formData: {script: true}
}

$('#fileupload').fileupload();
```

### 결과)csrf 토큰 넘기기 

- 본래는, django에서 csrf token을 넘길 때 form 태그 안에서 넘긴다. 이 라이브러리에서는, form태그를 쓰지 않고도, form을 쓴 것 처럼 데이터를 넘길 수 있음. 

```html 
  <form method="post">{% csrf_token %}
```
