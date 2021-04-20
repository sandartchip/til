
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


즉, 모델의 필드명(file)이 해당 필드에 대응하는 input 요소의 id값(id_file)이 된다.


