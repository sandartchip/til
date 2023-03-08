```scipy.stats.percentileofscore
scipy.stats.percentileofscore(a, score, kind='rank', nan_policy='propagate')[source]
```


- Compute the percentile rank of a score, relative to a list of scores.

- A percentileofscore of, for example, 80% means that 80% of the scores in a are below the given score. 
- a: array_like, Array to which score is compared.
- score: Scores to compute percentiles for.
- Percentile-position of score (0-100) relative to a.

```python
stats.percentileofscore([1, 2, 3, 4], 3)
>>75.0
```

