


- 장고에서는 직접 회원 모델을 만들기보단 auth에서 제공하는 User 모델을 이용하여 기능을 구현하길 강력하게 권고한다.
- 기본적인 User모델의 상속 구조는 다음과 같다.
```python
models.Model
class AbstractBaseUser : models.Model 상속
class AbstractUser : AbstractBaseUser 상속
class User : AbstractUser 상속
```

#### User 모델을 만드는 4가지 방법
1. Proxy Model
- 기존 User 모델을 직접 상속한다.
- Meta 클래스에서 proxy =True 속성을 추가한다.
- DB 스키마에 영향을 주지 않는다.
- 기존 User 모델에서 DB 스키마 외에 최소한의 변경사항만을 적용할 때 사용한다.
- 모델 설계의 자유도가 가장 낮다.
```python
from django.contrib.auth.models import User
from .managers import PersonManager

class Person(User):
    objects = PersonManager()

    class Meta:
        proxy = True

    def do_something(self):
        ...
```

2. One-to-One
- 새로운 모델을 추가하여 기존 User 모델과 1:1 관계로 연결시켜 사용자 정보를 저장한다.
- 기존 User 모델과 관계됨으로서 auth 기능을 사용 할 수 있다.
- 프록시 방식에 비해 필드에 대한 자유도가 매우 높다.

```python
from django.db import models
from django.contrib.auth.models import User
    
class Profile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    nickname = models.CharField(max_length=20, blank=True)
    
    ...
```
