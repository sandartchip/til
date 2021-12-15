
## step1 
settings.py를 base.py로 바꿈

## step2
prod.py, local.py 추가,
```python
from .base import *
```
으로 base파일의 모든 내용 읽어 옴.



- 로컬에서 실행할 때
```
set DJANGO_SETTINGS_MODULE=config.settings.local (윈도우)

```

- 원격에서 실행할 때
```
set DJANGO_SETTINGS_MODULE=config.settings.prod
```

쉘에서 실행
https://wikidocs.net/75560
