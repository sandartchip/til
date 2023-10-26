
## Bulk save (Bulk_create)

- 이 메서드는 **제공된 객체 목록을 데이터베이스에 효율적인 방식으로 삽입** 함.  
(일반적으로 객체 수에 상관없이 단 한 번의 쿼리만 수행)
- 그리고 생성된 객체를 제공된 순서와 동일한 순서로 목록으로 반환함.


```python

users = Users.objects.all()

for user in users:
  Notification(user=user, contents="반갑습니다.").save()
```

- 위와 같은 방법으로 for문을 돌며 다수의 object를 만들어 낼 경우, save() 한 번당 DB와의 connection이 한 번 발생, insert 수행.
- 서비스에 큰 부하가 생겨 장애를 야기할 수 있음


```python
users = User.objects.all()

new_noti_list = [Notification(user=user, contents="반갑습니다.") for user in users]
Notification.objects.bulk_create(new_noti_list)
```

- 이 때 사용하는 것이 bulk operation이며 이 bulk를 사용하면 다수의 레코드를 생성, 업데이트 할 때 한 번의 커넥션 만으로 insert 혹은 update를 수행할 수 있다.
- 반복문으로 db insert를 한 경우보다 bulk operation이 응답시간이 5배 이상 증가한 경우도 있다고 한다. 
