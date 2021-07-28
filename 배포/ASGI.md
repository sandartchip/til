
## WSGI로 비동기 처리했을 때의 한계 

- Django has support for writing asynchronous (“async”) views, 
- along with an entirely async-enabled request stack **if you are running under ASGI.** 

- **Async views will still work under WSGI**, but with performance penalties, and without the ability to have efficient long-running requests.

- Under a WSGI server, async views will run in their own, one-off event loop. 

- This means you can use async features, like concurrent async HTTP requests, without any issues, but **you will not get the benefits of an async stack.**


## Async stack 의 장점

- The main benefits are the **ability to service hundreds of connections ### without using Python threads ### **.

- This allows you to use slow streaming, long-polling, and other exciting response types.

- If you want to use these, you will need to deploy Django using ASGI instead.

- You will only get the benefits of a fully-asynchronous request stack **if you have no synchronous middleware loaded into your site.**
