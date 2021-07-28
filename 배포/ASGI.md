
Django has support for writing asynchronous (“async”) views, 
along with an entirely async-enabled request stack **if you are running under ASGI.** 

**Async views will still work under WSGI**, but with performance penalties, and without the ability to have efficient long-running requests.

