
- 모든 ModelForm은 save() 메소드를 가지고 있다.
- 이 함수는, form에 bound된 데이터로부터 데이터베이스 Object를 생성하고 저장한다.

```python

from myapp.models import Article
from myapp.forms import ArticleForm

f = ArticleForm(request.POST) # Create a form instance from POST DATA
new_article = f.save() # save a new Article object 

# create a form to edit an existing Article, but use POST data to populate the form.

a = Article.objects.get(pk=1)
f = ArticleForm(request.POST, instance=a)
f.save()

```
