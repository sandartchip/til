
#### gitignore 시킬 거


- collectstatic 된 static 폴더 
  collectstatic 을 하면, 앱/static 폴더에 있던 정적 파일들이 프로젝트명/static폴더로 이동함 
  
  -> 프로젝트명/static 폴더의 결과들도 서버에 올라가야, 변경된 static과 css가 제대로 반영 됨. 

  혹은, 도커에서 빌드할 때 python manage.py collectstatic 후 python manage.py runserver 적용.


