

## HttpResponse

html파일, 이미지 등 다양한 응답을 해줄 수 있다. 

하나의 함수는 최소 하나의 HttpResponse를 반환해야 한다. 이는 views에서 검사하는게 아니라 middleware에서 검사하게 된다. 

```
# config/settings.py

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

middleware는 다음과 같이 app을 감싸고 있으면서, request가 들어올 때는 적절하게 가공해주고, response가 나갈 때도 확인을 해 준다.   

![image](https://user-images.githubusercontent.com/15938354/114992179-6c78a280-9ed5-11eb-8f48-bbb15a296aed.png)  


