

- CSRF 공격을 방어하기 위한 다양한 방법 존재
- Django는 기본적으로 Csrf Token 사용 
- POST에 대해서만 csrf token 발급 및 체크 
- CSRFViewMiddleware은 Middleware 설정에서 기본적으로 활성화 되어 있다.

- POST 양식을 사용하는 템플릿에서 form 태그 안에 {% csrf_token %} 태그를 사용 
