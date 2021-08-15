# 요청과 응답


![image](https://user-images.githubusercontent.com/15938354/129476508-1ae61707-2ccf-47dd-be74-7a67115fb467.png)


- WAS는 웹 브라우저로부터 Servlet요청을 받으면,
**요청올 때 가지고 있던 정보를 HttpServletRequest객체를 생성하여 저장**함.

- 웹 브라우저에게 응답을 보낼 때 사용하기 위하여 HttpServletResponse객체를 생성함.

- WAS는 생성한 HttpServletRequest, HttpServletResponse 객체를 서블릿에게 전달함.
 

## HttpServletRequest

- http프로토콜의 request정보를 서블릿에게 전달하기 위한 목적으로 사용
- 헤더정보, 파라미터, 쿠키, URI, URL 등의 정보를 읽어 들이는 메소드를 가지고 있음.
- Body의 Stream을 읽어 들이는 메소드를 가지고 있습니다.


## HttpServletResponse

- WAS는 어떤 클라이언트가 요청을 보냈는지 알고 있고, 해당 클라이언트에게 응답을 보내기 위한 HttpServletResponse객체를 생성하여 서블릿에게 전달함.
- 서블릿은 해당 객체를 이용하여 content type, 응답코드, 응답 메시지등을 전송합니다.
