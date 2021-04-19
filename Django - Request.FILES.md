

A view handling this form will **receive the file data in request.FILES**,
 which is a **dictionary** 
 **containing a key for each FileField **
 (or ImageField, or other FileField subclass) in the form. 
 
 So the data from the above form would be accessible as request.FILES['file'].

Note that request.FILES will only contain data if the request method was POST, 
at least one file field was actually posted, 
and the <form> that posted 
the request has the attribute enctype="multipart/form-data". 
 
Otherwise, request.FILES will be empty.

Most of the time, you’ll pass the file data from request into the form as described in Binding uploaded files to a form. This would look something like:

출처: 공식문서 
