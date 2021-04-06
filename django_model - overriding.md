
장고에서 모델의 함수를 오버라이딩 할 수 있다.

delete함수를 오버라이딩 시키려고 하니 오버라이딩이 되지 않는 문제가 발생했다.


```
#models.py
class InputFile(models.Model):
    #file = models.FileField(null=False, upload_to="/media/"+date_upload_to) # job_id/파일명
    file = models.FileField(null=False, upload_to=date_upload_to, storage=OverwriteStorage())  # 프로젝트폴더/media/job_id/파일명에 저장
    job_id = models.CharField(max_length=45, default="0")

    def delete(self, *args, **kwargs): # 메소드 오버라이딩. remove가 아니라 delete라고..?

        if self.file:
            print("---삭제---")
            os.remove(os.path.join(settings.MEDIA_ROOT, self.file.path))

        super(InputFile, self).delete("test")
```

```

def remove_input_file(request): #파일 삭제 요청 시

    if request.method == 'POST':
        print("POST 요청")
        chkbox_elems = request.POST.getlist('file_chkbox') # 체크된 체크박스 리스트의 value값 가져오기

        for chkbox_elem in chkbox_elems:
            **remove_item = InputFile.objects.filter(id=chkbox_elem)** # queryset형태로 삭제할 아이템이 넘어옴.
            remove_item.delete()

```
를 수행하였다.
remove_item은 InputFile 객체를 특정 조건으로 필터링한 queryset이다.
remove_item에 delete 함수를 적용하였는데, 오버라이딩 된 delete함수가 아닌 기존의 delete함수가 적용되었다.

원인을 알 수 없어 고통받던 도중, 
Django 공식 문서(https://docs.djangoproject.com/en/3.1/topics/db/queries/)에서 
>
Keep in mind that this will, whenever possible, be executed purely in SQL, 
and so the delete() methods of individual object instances will not necessarily be called during the process. 
If you’ve provided a custom delete() method on a model class and want to ensure that it is called, 
you will need to “manually” delete instances of that model 
(e.g., by iterating over a QuerySet and calling delete() on each object individually) 
rather than using the bulk delete() method of a QuerySet.
```
을 발견하였다.


