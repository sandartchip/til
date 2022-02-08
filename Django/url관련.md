### url 규칙

- 브라우저에서 요청할 때 / 붙으나 안 붙으나 상관 없다.
- (http://localhost/api , http://localhost/api/)

장고 url에 슬래시 안 붙인 경우 -> 장고가 알아서 클라이언트에게 301 HTTP response(영구적인 URL 리디렉션)를 보내고 슬래시 붙인 주소로 자동 리다이렉트, 
그에 대한 HTTP response를 다시 클라이언트에게 보내준다.



### url 경로 - ajax와 템플릿 

나는 url(클라이언트)에서 요청하는 경로와

장고가 미리 알고 있는 경로인 템플릿의 경로가 자꾸 햇갈림.

ajax 요청은, 브라우저에 치는거랑 똑같고, urls.py의 경로 따름.
템플릿 디렉토리 몰라ㅠㅠ


- 뷰 에서-> template render은, settings.py에 template 경로 정해진거 보고 찾아가는 거임.


```python
# settings.py

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [ os.path.join(MAIN_APP_DIR, 'templates') ],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```
