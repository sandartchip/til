
### null, default, blank의 차이

### url, path의 차이
#### url
- Django 2.0 이전엔 url 사용
- django.conf.urls의 url로 라우팅
- 정규식 사용 

```python
   urlpatterns = [ url(r'^book/(?P<pk>\d)/$', views.BookDetail.as_view(), name='book_detail')]
```
#### path 
- Django 2.0 이후엔 path라는 간결한 모듈 등장
 
```python
   urlpatterns = [ path('bookmark/<int:pk>/', BookmarkDV.as_view(), name='detail')]
```


### os.mkdir 과 os.makedirs 
폴더 만들 때 os.mkdir은 1단 폴더만 만듬

```python
if (not os.path.isdir(result_folder_path)):
  os.makedirs(result_folder_path)
```
  
=>  /aaa/bbb/ccc같은 하위경로 폴더 생성가능


### foreign key 필드가 템플릿에 렌더링 되면?

models.py 

```python
class Upload(models.Model):
    #file = models.FileField(upload_to='images_test')
    file = models.FileField(upload_to=upload_filepath)
    **folder = models.ForeignKey(Folder, on_delete=models.CASCADE, default=-1, db_column="folder")** # 폴더 테이블의 id를 PK로 한 폴더 객체를 참조 해 온다. 
```

forms.py
```python
class UploadFileForm(forms.ModelForm):
    class Meta:
        model = Upload
        fields = ('file', 'folder',)
        widgets = {
            'file': forms.FileInput(attrs = {'id': 'file_id'}),
            'folder': forms.TextInput(attrs = {'id': 'folder_id'})
        }
```

template.html
```html
<p>
  <label for="folder_id">Folder:</label> 
  <input type="text" name="folder" value="-1" id="folder_id" required="">
</p>
```

views.py

```python
def submit_new_job(request):
    file_form = UploadFileForm(request.POST or None, request.FILES or None)
    if( file_form.is_valid()):
       folder =  file_form.cleaned_data['folder']  # 왜 object????? 
       folder_uuid_name = file_form.cleaned_data['folder'].name  
   
   return render(request, 'soyeon_pj/program/serotyper/after_submit.html', context)

```


after_submit.html
```html

<p class="job_id">Job ID: {{ folder_uuid_name }}</p>

```


html 템플릿 상에 **폴더의 id가 아닌, 폴더 객체 자체**가 렌더링된다. 
