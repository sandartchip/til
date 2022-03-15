
### Annotate

- 객체 별 요약을 생성할 수 있다.
- annotate() 메서드 내의 집계 함수의 인자로 필드명을 사용해야 한다.
- 예를 들어 다음과 같은 모델에서, 각 도서의 저자 수를 count()로 구한다면 다음과 같다.

#### 예시
```python
from django.db import models

class Author(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()
    
class Book(models.Model):
    name = models.CharField(max_length=300)
    pages = models.IntegerField()
    price = models.DecimalField(max_digits=10, decimal_places=2)
    rating = models.FloatField()
    authors = models.ManyToManyField(Author)
    publisher = models.ForeignKey(Publisher, on_delete=models.CASCADE)
    pubdate = models.DateField()
```

#### 예시 1 - 각 항목에 대한 집계 생성
```python
>>> from django.db.models import Count
>>> q = Book.objects.annotate(Count('authors'))
>>> q[0]
<Book: The Definitive Guide to Django>
>>> q[0].authors__count
2
>>> q[1].authors__count
1
```

#### 예시2  - 가장 책을 많이 출간한 출판사 TOP5

```python
>>> pubs = Publisher.objects.annotate(num_books=Count('book')).order_by('-num_books')[:5]
>>> pubs[0].num_books
```


https://docs.djangoproject.com/en/4.0/topics/db/aggregation/
