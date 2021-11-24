

- 기존 modelform을 view에서 받아 save 시킬 때 필요한 정보를 추가시키기위해 commit을 false 시키고 해당 form을 받은 변수를 save시킨다. 

- 이때 modelform에 manytomany 필드가 있을 경우 manytomany필드는 저장이 되지않는다. 
- 그러므로 modelform에 대한 save를 save_m2m()으로 따로 저장시켜 주어야한다. (뭔가 불편하다)


ex)

안되는 경우
```
f = form.save(commit=False)
kind = VacationKind.objects.get(kind=request.POST['kind'])
f.kind = kind
f.save()
```

save_m2m을 사용해 저장시킴
```
f = form.save(commit=False)
kind = VacationKind.objects.get(kind=request.POST['kind'])
f.kind = kind
f.save()
form.save_m2m()
```
