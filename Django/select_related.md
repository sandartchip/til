
# search 
```python
    job_list = Job.objects.select_related('result_folder').filter(Q(result_folder__name__contains=search_input) )
```

# order by 

https://stackoverflow.com/questions/1611892/django-orm-select-related-and-order-by-with-foreign-keys
