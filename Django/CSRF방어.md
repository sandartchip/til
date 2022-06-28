
### Cross Site Request Forgery protection

The CSRF middleware and template tag provides easy-to-use protection against Cross Site Request Forgeries. 
This type of attack occurs when a malicious website contains a link, a form button or some JavaScript that is intended to **perform some action on your website**,
using the **credentials of a logged-in user** who visits the malicious site in their browser. 

A related type of attack, **‘login CSRF’**, where an attacking site tricks a user’s browser into logging into a site with someone else’s credentials, is also covered.

The first defense against CSRF attacks is to ensure that GET requests (and other ‘safe’ methods, as defined by RFC 7231#section-4.2.1) are side effect free. Requests via ‘unsafe’ methods, such as POST, PUT, and DELETE, can then be protected by following the steps below.


### How to use it
To take advantage of CSRF protection in your views, follow these steps:

1. The CSRF middleware is activated by default in the MIDDLEWARE setting. If you override that setting, remember that 'django.middleware.csrf.CsrfViewMiddleware' should come before any view middleware that assume that CSRF attacks have been dealt with.

If you disabled it, which is not recommended, you can use csrf_protect() on particular views you want to protect (see below).

2. In any template that uses a POST form, use the csrf_token tag inside the <form> element if the form is for an internal URL, e.g.:

```html
  <form method="post">{% csrf_token %}
```
This should not be done for POST forms that target external URLs, since that would cause the CSRF token to be leaked, leading to a vulnerability.

    
3. In the corresponding view functions, ensure that RequestContext is used to render the response so that {% csrf_token %} will work properly. If you’re using the render() function, generic views, or contrib apps, you are covered already since these all use RequestContext.
    
  

- CSRF 공격을 방어하기 위한 다양한 방법 존재
- Django는 기본적으로 Csrf Token 사용 
- POST에 대해서만 csrf token 발급 및 체크 
- CSRFViewMiddleware은 Middleware 설정에서 기본적으로 활성화 되어 있다.

- POST 양식을 사용하는 템플릿에서 form 태그 안에 {% csrf_token %} 태그를 사용 
