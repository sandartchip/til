
- get은 그 model 객체 하나를 리턴하고 
- filter은 쿼리셋을 리턴함. values로 여러개를 가져옴.

```python
# This list contains a Blog object.
>>> Blog.objects.filter(name__startswith='Beatles')
<QuerySet [<Blog: Beatles Blog>]>

# This list contains a dictionary.
>>> Blog.objects.filter(name__startswith='Beatles').values()
<QuerySet [{'id': 1, 'name': 'Beatles Blog', 'tagline': 'All the latest Beatles news.'}]>

- values()는 dictionary의 리스트를 가져 옴. 

```
[{'comment_id': 1}, {'comment_id': 2}]

```

- values_list는 튜플로 가져 옴. 
```
[(1,), (2,)]
```

- values_list를 single field로 가져 오려면 ->
```
[1, 2]
```
