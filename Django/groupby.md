
## annotate 
- annotate 는 group by 의 역할을 한다. 

#### 예시
```python
    qc_stat_queryset = Process.objects.values('qc1').filter(sample__company_id__in=company_list_per_sample).annotate(process_cnt=Count('qc1'))
```
Process에서 qc1 필드 기준 group by 함. 
