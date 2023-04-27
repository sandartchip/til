
![image](https://user-images.githubusercontent.com/15938354/234776603-21227cd1-b1f2-474f-a6d5-c87a64a81283.png)


```python
df_result = pd.DataFrame(index=self.li_new_sample_name, columns=self.li_phenotype)
```

바코드번호가  index 일 때
컬럼별로 [바코드번호,질병명] 이렇게 들고오려면

```python

for col in df_result.columns:
  df_result.loc[self.serialnumber, col]
```

index, column명으로 추출한다
