
폴더 만들 때 os.mkdir은 1단 폴더만 만듬

```python
if (not os.path.isdir(result_folder_path)):
  os.makedirs(result_folder_path)
```
  
=>  /aaa/bbb/ccc같은 하위경로 폴더 생성가능
