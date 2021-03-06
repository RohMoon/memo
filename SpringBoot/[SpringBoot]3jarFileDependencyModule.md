# [spring Boot] JAR파일 독립 실행
- Spring boot maven plugin에 관한 내용이다.<br>
스프링부트 프로젝트를 만들고 개발을 할 때는 intellij에서 실행시켜서 확인하면 된다.<br><br>
그러나 이 어플리케이션을 배포 or 도커 이미지로 만들 때는 JAR 패키지로 패키징하여 JAR파일을 실행하는 방법이 유용하게 사용된다.<br><br>
먼저, `mvn clean`을 해준다. (`target` 하위를 모두 비우는 것 )
- ![img_9.png](img_9.png)<br><br>
그 후 mvn package를 해준다.<br><br>
- ![img_10.png](img_10.png)<br><br>
- 그럼 target에 jar 파일이 생긴다.<br><br>
- ![img_11.png](img_11.png)<br><br>
- 이 `jar`파일로 어플리케이션을 실행시킬 수 있다. (`target` 디렉토리에서 실행)
- `java - jar "jar파일이름"`<bR>
- 이렇게 jar파일로 만들면 수많은 의존성들도 만들어진 `jar`파일에 모두 들어있다.<br><br>
- 스프링부트는 내장 `JAR`로 만들어진 `JAR`파일 안에 여러 `JAR`파일들을 묶어놓고, 그 `JAR`파일들을 읽을 수 있는 파일들을 만들어 놓았다.<br><br>
- `org.springframework.boot.loader.jar.JarFile`을 이용하여, 내장 `JAR` 파일을 읽고,
- `org.springframework.boot.loader.Launcher`를 사용하여 실행한다.<br><br>
- 즉, 스프링부트는 <b> 독립적으로 실행가능한 어플리케이션</b>이다.

- 독립적으로 실행가능한 어플리케이션이 스프링부트의 주요 목적이다.
- pom.xml의 Spring-boot-maven-plugin이 해주는 일이 바로 패키징이다.
jar 안에 jar 파일들을 그대로 묶어둘 수 있도록 지원 해서 하나의 jar 파일로 패키징할 수있다.
모든 명령어는 프로젝트의 홈 디렉토리에서 실행하면 된다.
- 아래는 대표적으로 쓰이는 명령어이다.
- mvn clean
- mvn package ->  실행 가능한 JAR파일 "하나가" 생성된다.
- mvn clean package -->한번에 실행할 수도 있다.
- mvn package- DskipTests --> test는 건너뛴다.
- java- jar 생성된_jar_파일_이름  --> 실행한다.
