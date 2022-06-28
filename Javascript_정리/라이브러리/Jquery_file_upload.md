
### 기본 플러그인 
https://github.com/blueimp/jQuery-File-Upload/wiki/Basic-plugin


## csrf 토큰 넘기기 

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
   
