# [Spring Boot] SpringApplication

스프링 부트로 프로젝트를 실행할 때 Application 클래스를 만든다.
클래스명은 개발자가 프로젝트에 맞게 설정할 수 있지만 큰 틀은 아래와 같다.
```java
@SpringBootApplication
public class Application {

	public static void main(String[] args) {
		SpringApplication.run(Application.class, args);
	}

}
```

`@SpringBootApplication` 어노테이션을 통해 스프링 Bean을 읽어와 자동으로 생성해준다.

이 어노테이션이 있는 파일 위치부터 설정들을 읽어가므로 반드시 프로젝트의 최상단에 만들어야 한다.

`SpringApplication.run()`으로 해당 클래스를 run하면 내장 WAS를 실행한다. 내장 WAS의 장점으로는 개발자가 따로 톰캣과 같은 외부 WAS를 설치 후 설정해두지 않아도 애플리케이션을 실행할 수 있다.

또한, 외장 WAS를 사용할 시 이 프로젝트를 실행시키기 위한 서버에서 모두 외장 WAS의 종류와 버전, 설정을 일치시켜야 한다. 따라서 내장 WAS를 사용하려면 이런 신경은 쓰지 않아도 되기 때문에 매우 편리하다.

> 내장 WAS
> Spring Boot는 서버에 별도의 WAS를 설치할 필요가 없도록 내장 WAS를 사용한다. 따라서 외부에 별도로 추가 서버를 두지 않고 Spring Boot Jar 파일만 실행하면 된다.
> 
> Spring Boot는 내장 WAS를 사용할 것을 권장하는데 그 이유는 언제 어디서나 같은 환경에서 스프링 부트를 배포할 수 있기 때문이다. 외부 WAS를 사용한다면 서버를 배포할 때마다 모든 서버가 같은 WAS 환경을 구축해야 해서 비효율적이다.

---

참조

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/Spring/%5BSpring%20Boot%5D%20SpringApplication.md

https://velog.io/@jwkim/spring-boot-internal-was