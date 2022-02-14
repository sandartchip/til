
# search 
```python
    job_list = Job.objects.select_related('result_folder').filter(Q(result_folder__name__contains=search_input) )
```

select related는 각각의 lookup마다 SQL의 JOIN을 실행하여 테이블의 일부를 가져오고, SELECT ..FROM에서, 

#### 공식 문서 설명
- 외래키 관계를 가진 쿼리를 실행할 때, 추가적인 관계된-객체 데이터를 선택하여 쿼리셋을 리턴한다. (selecting additional related-object data when it executes its query. )
- 이것은 단일한 성능 부스터이다 단일 더 complex한 쿼리를 리턴,할 수 있는. 


# order by 

https://stackoverflow.com/questions/1611892/django-orm-select-related-and-order-by-with-foreign-keys
