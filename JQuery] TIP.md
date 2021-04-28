
.val()

요소의 value를 가져옴.

ex)

```html

<input type="hidden" id="test_id" class="test_class" name="test_name" value="test">

```

```javascript 

var value_by_id = $('#test_id').val();

var value_by_class = $('.test_class').val();

var value_by_name = $('input[name=test_name]').val();

```
