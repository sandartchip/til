![image](https://user-images.githubusercontent.com/15938354/234776082-82f2dc39-61f6-458b-b0db-8485896f82e1.png)

```python
df_result = pd.DataFrame(index=self.li_new_sample_name, columns=self.li_phenotype)
```

바코드번호가  index 일 때
[바코드번호,질병명] 이렇게 들고오려면

```
df_result.loc[self.serialnumber, col]
```
