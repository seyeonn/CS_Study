# Bean Scope

![spring-bean](https://user-images.githubusercontent.com/38287375/187075110-1219cad2-fdd0-4fdd-a6ef-2e0af45c1040.png)

> - Bean은 스프링에서 사용하는 POJO(Plain Old Java Object) 기반 객체이다.
> - Beans는 애플리케이션의 핵심을 이루는 객체이며 Spring IoC 컨테이너에 의해 인스턴스화, 관리, 생성된다.
> - Beans는 우리가 컨테이너에 공급하는 설정 메타 데이터(XML 파일)에 의해 생성된다.
> - 애플리케이션의 객체가 지정되면 해당 객체는 getBean() 메서드를 통해 가져올 수 있다.


상황과 필요에 따라 Bean을 사용할 때 하나만 만들어야 할 수도 있고, 여러개가 필요할 때도 있고, 어떤 한 시점에서만 사용해야할 때가 있을 수 있다.

이를 위해 Scope를 설정해서 Bean의 사용 범위를 개발자가 설정할 수 있다.

우선 따로 설정을 하지 않을 경우 Spring에서 Bean은 자동으로 `Singleton`으로 생성된다.

`Singleton`패턴처럼 특정 타입의 Bean을 딱 하나만 만들고 모두 공유해서 사용하기 위함이다. 보통은 Bean을 이렇게 하나만 만들어 사용하는 경우가 대부분이지만, 요구사항이나 구현에 따라 아닐 수도 있다.

따라서 Bean Scope는 싱글톤 말고도 여러가지를 지원해준다.

## Scope 종류

1. Singleton
	- 해당 Bean에 대해 IoC 컨테이너에서 단 하나의 객체로만 존재한다.
	- Singleton Bean은 Spring 컨테이너에서 한 번 생성된다. (컨테이너가 사라질 때 Bean도 제거)
2. Prototype
	- 해당 Bean에 대해 다수의 객체가 존재할 수 있다.
	- Prototype Bean은 모든 요청에서 새로운 객체를 생성하는 것을 의미한다.
	- 즉, Prototype Bean은 의존성 관계의 Bean에 주입될 때 새로운 객체가 생성되어 주입된다.
3. Request
	- 해당 Bean에 대해 하나의 HTTP Request의 라이프 사이클에서 단 하나의 객체로만 존재한다.
4. Session
    - 해당 Bean에 대해 하나의 HTTP Session의 라이프사이클에서 단 하나의 객체로만 존재한다.
5. Global Session
    - 해당 Bean에 대해 하나의 Global HTTP Session의 라이프사이클에서 단 하나의 객체로만 존재한다.

> Request, Session, Global Session은 MVC 웹 어플리케이션에서만 사용함

Scope들은 Bean으로 등록하는 클래스에 어노테이션으로 설정해줄 수 있다.

```
import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Service;
 
@Scope("prototype")
@Component
public class UserController {
}
```

---

참조

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/Spring/%5BSpring%5D%20Bean%20Scope.md

https://gmlwjd9405.github.io/2018/11/10/spring-beans.html