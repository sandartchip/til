
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
