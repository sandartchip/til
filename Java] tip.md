![image](https://user-images.githubusercontent.com/15938354/116842077-40b82500-ac16-11eb-86c1-27e4e4b72593.png)

### JRE(Java SE Runtime Environment)
- 컴파일된 자바 프로그램을 실행시킬 수 있는 자바 환경

- JAVA언어로 작성된 프로그램을 실행하기 위해선 JRE(Java SE Runtime Environment)가 필요하다. 

- 보통 사용자 입장에서 JAVA를 설치한다는 것은 JRE를 설치하는 것을 말한다.
(- JAVA언어를 사용하는 개발자가 아니라 JAVA언어로 만들어진 프로그램을 실행하는 사용자는, JRE만 컴퓨터에 설치하면 된다.)

- JAVA언어를 사용하는 개발자는 JAVA언어로 작성된 소스(Source)를 컴파일하고 관리할 필요가 있다.

- 이때 사용되는 도구를 JDK(Java SE Development Kit)라고 말한다.

- JDK안에는 JRE도 포함되어 있다.(컴파일한 결과를 실행하기 위해서는 JRE가 필요하기 때문)


### JDBC

- Java Database Connectivity 
- 자바에서 DB 프로그래밍을 하기 위해 사용되는 API



### JVM

- JVM은 프로그램을 실행하는 자바 플랫폼 구성요소다.
- JRE는 JVM을 생성하는 디스크 상의 부분이다.
- JDK는 개발자들이 JVM과 JRE에 의해 실행되고 구동될 수 있는 자바 프로그램을 생성할 수 있게 해준다.

### JDK

모든 JDK는 자바 애플리케이션 구동에 이용되는 환경 JRE뿐만 아니라, 자바 컴파일러도 포함하고 있다. 
컴파일러는 평범한 텍스트인 원시(Raw) .java 파일을 받아서 실행 가능한 .class 파일로 만드는 기능이 있는 소프트웨어다. 
곧 컴파일러 사용을 볼 수 있을 것이다. 우선, 개발 환경으로 JDK를 다운로드해 설정하는 방법을 알려 줄 것이다.

JDK 최신버전은 9이다. 
그러나 현재 가장 많이 사용되는 버전은 8이다.

#### JDK가 운영체제별로 설치파일을 제공하는 이유는 무엇입니까?
#### 자바로 작성된 프로그램을 실행하려면 JRE만 설치하면 됩니다. 이때는 환경변수를 설정할 필요가 없습니다.
    그런데, JDK를 설치할 때는 환경변수를 설정해야 합니다. 환경변수를 설정하는 이유가 무엇일까요?
#### 현재 설치된 JDK보다 높은 버전의 JDK를 설치했습니다. 이때 수정해야 할 환경변수는 무엇일까요?


### Java Code convention

클래스명 : 첫글자를 대문자로
프로젝트명, 패키지명 : 소문자

### JAVA SE, EE

#### JAVA SE (Java Standard Edition)
- SE(Standard Edition) 는 일반 자바프로젝트 버전.
- 가장 기본이 되는 에디션. 
- 흔히 자바 언어라고 하는 대부분의 패키지가 포함
- 주요 패키지로는 java.lang.*, java.io.*, java.util.*, java.awt.*, javax.rmi.*, javax.net.* 등이 있다.


#### JAVA EE (Java Enterprise Edition)
- 자바로 구현되는 웹 프로그래밍에서 가장 많이 사요되는 JSP, Servlet을 비롯
데이터베이스에 연동하는 JDBC, 그 외에도 JNDI, JTA, EJB 등의 기술이 포함. 
- Java EE는 Java SE의 API에 추가로(lib 디렉토리에 포함되어 있는 JAR파일들)의 차이이다. 



참고자료
https://210life.tistory.com/entry/Java-EE와-Java-SE의-차이점
https://www.boostcourse.org/web316/lecture/16680?isDesc=false

https://www.itworld.co.kr/news/110817

https://goodgid.github.io/Java-JDK-JRE/
