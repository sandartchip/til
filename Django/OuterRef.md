

### OuterRef

- 외부 테이블의 데이터를 참조한다.

- 서브쿼리를 실행할 때, 다른 테이블을 참조해야 할 필요가 있을 경우에 사용한다. 

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

위의 결과를 쿼리로 변환하면, 아래와 같이 나온다.
```sql
SELECT "item_base"."no",
       "item_base"."name",

  (SELECT U0."name"
   FROM "item_items" U0
   WHERE U0."base_no" = ("item_base"."no")
   LIMIT 1) AS "item_name"
FROM "item_base"
```

만약 비교하고 싶은 컬럼이 pk가 아닌 일반 컬럼일 경우, 일반 컬럼을 작성하여 비교할 수 있다.

```python
from item.models.base import Items, Base
from django.db.models import OuterRef, Subquery


item_qs = Items.objects.filter(
    base_no=OuterRef('cnt')
)
qs = Base.objects.annotate(
    item_name=Subquery(
        item_qs.values('name')[:1]
    )
)
```

해당 파이썬 코드는 다음 sql로 변경된다.
```sql
SELECT "item_base"."no",
       "item_base"."cnt",
       "item_base"."name",

  (SELECT U0."name"
   FROM "item_items" U0
   WHERE U0."base_no" = ("item_base"."cnt")
   LIMIT 1) AS "item_name"
FROM "item_base"
```

#### 참고 자료 
https://brownbears.tistory.com/422
