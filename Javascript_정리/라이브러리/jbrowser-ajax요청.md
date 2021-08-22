
![image](https://user-images.githubusercontent.com/15938354/130358757-f238e45e-28a5-40ba-8fbe-9747003bc9f8.png)


- jbrowser 라이브러리에서 static 폴더에 있는 Query.db로 ajax 요청 했을 때 못 찾는 문제 
- **ajax 요청 시 url 속성의 url로, 새로운 요청 보냄.**
- 장고 wsgi 웹서버는 해당 url로 요청 받았기 때문에 urls.py를 찾음.
- urls.py에는 url에서 static 경로로 요청 시 STATIC_ROOT + STATIC URL 경로로 의 static파일들 찾도록 설정해 놓음.
- 므로, collect static 
