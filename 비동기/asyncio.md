# 이벤트 루프

- 이벤트 루프는 모든 asyncio 응용 프로그램의 핵심이다.
- 이벤트 루프는 비동기 태스크 및 콜백을 실행
- 네트워크 IO 연산 수행, 자식 프로세스 실행
- 응용 프로그램 개발자는 일반적으로 asyncio.run()과 같은 고수준의 asyncio 함수를 사용해야 하며, 루프 객체를 참조하거나 메서드를 호출할 필요가 없다. 

https://docs.python.org/ko/3/library/asyncio-eventloop.html



# asyncio.run( 함수() )

- 전달된 코루틴을 실행
- asyncio 이벤트 루프와 비동기 제너레이터의 파이널리제이션과 쓰레드 풀 닫기를 관리
- 항상 새 이벤트 루프를 만들고, 끝에 이벤트 루프를 닫는다.
- asyncio 프로그램의 **메인 진입 지점**으로 사용하고, 이상적으로는 한 번만 호출해야 한다.


## 에러상황 
```
coroutine 'test' was never awaited 
```
-> 코루틴 함수가 호출되었지만 기다리지 않을 때 (await coro() 대신 coro()일 때)
