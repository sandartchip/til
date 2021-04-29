
### form에서, form.as_table로 템플릿에서 자동 로드하면 로드되는 결과

```html
  <label for="id_file">File:</label>
  <input type="file" name="file" required="" id="id_file">
```


```python  
class Upload(models.Model):
    file = models.FileField(upload_to='images_test')

    def __str__(self):
        return str(self.pk)
```

모델에서, FileField형의 필드를 만들면

해당 파일 모델에 대해서, 
- 레이블 태그의 label for 속성이 **id_필드명**으로 지정되고,
- input 태그의 name과 type이 **해당 필드명으로** 지정된다. 


### form 커스터마이징 

attr함수를 이용하여 커스터마이징 가능하다. 

```python

class UploadFileForm(forms.ModelForm):
    class Meta:
        model = Upload
        fields = ('file', 'folder',)
        widgets = {
            'file': forms.FileInput(attrs = {'id': 'file_id'}),
            'folder': forms.HiddenInput(attrs = {'id': 'folder_id'})
        }
```


### cleaned_data

cleaned_data로 form의 데이터 가져오는건 is_valid()함수를 호출 한 이후에만 가능하다. 

