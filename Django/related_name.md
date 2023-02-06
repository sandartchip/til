
```python
class Comment(models.Model):
    User = models.ForeignKey(User, on_delete=models.CASCADE, related_name= ? )
```

- 역참조에 사용함. 
- 즉, user객체에서 comment을 가져 올 때 사용함.

user.[?].all() 뒤에 오는 이걸 지정하는게 related name.


```python

user.comment.all() 

```