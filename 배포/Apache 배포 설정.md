

## 1. Apache 설치 
```
apt-get install apache2
```

## 2. 장고의 wsgi.py 파일 수정 
```python
import os, sys

# 추가해야 할 부분 
path = os.path.abspath(__file__+'/../..')
if path not in sys.path:
	sys.path.append(path) 
# 여기까지
 
from django.core.wsgi import get_wsgi_application

os.environ.setdefault("DJANGO_SETTINGS_MODULE", "[project_name].settings")
 
application = get_wsgi_application()
```
