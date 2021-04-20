
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
- 레이블 태그(label for 속성이 id_필드명)으로 지정되고,
- input 태그(name과 type이 해당 필드명으로)가 생긴다. 



