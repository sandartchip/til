
### db_column?

장고에서 외래키를 사용할 때는 

컬럼명 = models.ForeignKey('참조할 클래스명', 옵션) 을 사용한다. 


그러면 참조할 클래스의 컬럼명은 어디에 있나?
=> migrate를 시키면, 장고에서 참조한 테이블의 PK 컬럼명을 참조한 컬럼명_id 필드를 참조하게 된다.

원래 있던 외래키 필드명을 참조하게 하려면, db_column="컬럼명"을 하면 해결.


ex)
```python

class Folder(models.Model):
    id = models.AutoField(primary_key=True)  # Auto Increment
    name = models.CharField(max_length=200, default="") # UUID로 이루어진 폴더명.
    created_date = models.DateTimeField(null=True, blank=True, auto_now_add=True)

class Upload(models.Model):
    file = models.FileField(upload_to='images_test')
    folder = models.ForeignKey(Folder, on_delete=models.CASCADE, default=-1)
```

migrate시키면

![image](https://user-images.githubusercontent.com/15938354/116501977-354ebc00-a8ed-11eb-8f5b-e443b21da78c.png)

내가 원하는 folder필드가 아닌, folder_id를 참조하였다. 


```
class Upload(models.Model):
    file = models.FileField(upload_to='images_test')
    folder = models.ForeignKey(Folder, on_delete=models.CASCADE, default=-1, **db_column="folder"**)
```

![image](https://user-images.githubusercontent.com/15938354/116502072-83fc5600-a8ed-11eb-996f-d1873a6744d4.png)

