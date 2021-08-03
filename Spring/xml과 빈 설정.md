Engine.java
``` java
package kr.or.connect.diexam01;

public class Engine {
	public Engine() {
		System.out.println("Engine 생성자");
	}
	
	public void exec() {
		System.out.println("엔진이 동작합니다.");
	}
}
```

Car.java
```java
package kr.or.connect.diexam01;

public class Car {
	Engine v8;
	
	public Car() {
		System.out.println("Car 생성자");
	}
	
	public void setEngine(Engine e) {
		this.v8 = e;
	}
	
	public void run() {
		System.out.println("엔진을 이용하여 달립니다.");
		v8.exec();
```

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
	
	<bean id="userBean" class="kr.or.connect.diexam01.UserBean"></bean>
	<bean id="e" class="kr.or.connect.diexam01.Engine"></bean>
	<bean id="c" class="kr.or.connect.diexam01.Car">
		<property name="engine" ref="e"></property> <!-- property는 함수와 대응 -->
	</bean>
</beans>
```

위의 XML 설정은,

```

Engine e = new Engine();
Car c = new Car();
c.setEngine(e);

```

과 같다.
