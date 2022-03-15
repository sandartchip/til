
### OuterRef

- 외부 테이블의 데이터를 참조한다.

- 서브쿼리를 실행할 때, 다른 테이블을 참조해야 할 필요가 있을 경우. 

```python
class Base(models.Model):
    no = models.BigAutoField(primary_key=True)
	cnt = models.IntegerField()
    name = models.CharField(max_length=100)


class Items(models.Model):
    no = models.BigAutoField(primary_key=True)
    name = models.CharField(max_length=100)
    base_no = models.ForeignKey(Base, db_column='base_no')
```

```python
item_qs = Items.objects.filter(
    base_no=OuterRef('pk')
)
qs = Base.objects.annotate(
    item_name=Subquery(
        item_qs.values('name')[:1]
    )
)
```

