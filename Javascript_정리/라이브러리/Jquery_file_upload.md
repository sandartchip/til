
### 기본 플러그인 
https://github.com/blueimp/jQuery-File-Upload/wiki/Basic-plugin


### API 설명
(https://github.com/blueimp/jQuery-File-Upload/wiki/API)

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

### csrf 토큰 넘기기 

```html
<div id="upload_file">
  파일 업로드
  <input id="fileupload" type="file" name="files" multiple data-url="{% url 'main:upload_file' %}" data-form-data='{"csrfmiddlewaretoken": "{{ csrf_token }}"}'>
</div>
```

- 본래는, django에서 csrf token을 넘길 때 form 태그 안에서 넘긴다.

```html 
  <form method="post">{% csrf_token %}
```



   
