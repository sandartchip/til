
## annotate

```sql

SELECT sample.company_id, company.name, COUNT(sample.company_id) AS sample_cnt FROM main_sample INNER JOIN company ON sample.company_id = company.id 
WHERE sample.company_id IN (1,3,4,5)
GROUP BY sample.company_id, company.name 
```

values 가 group by 할 필드를 정한다. 

```python
company_list_per_sample = Sample.objects.values('company_id')
.filter(company_id__in=company_list)
.annotate(sample_cnt=Count('company_id'))
.values("company_id", "company_id__name", "sample_cnt")
                                                                                                   
```
