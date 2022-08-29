# Spring MVC Framework

![springmvc-architecture](https://user-images.githubusercontent.com/38287375/187876107-5bbf8d42-f5eb-4407-be7d-10f126f61c66.png)

1. Model
	- 애플리케이션의 상태(data)를 나타낸다.
	- 일반적으로 POJO로 구성된다.
	- Java Beans
2. View
	- 디스플레이 데이터 또는 프리젠테이션
	- Model Data의 렌더링을 담당하며 HTML Output을 생성한다.
3. Controller
	- View와 Model 사이의 인터페이스 역할
	- Model/View에 대한 사용자 입력 및 요청을 수신하여 그에 따라 적절한 결과를 Model에 담아 View에 전달한다.
	- 즉, Model Object와 이 Model을 화면에 출력할 View Name을 반환한다.
	- Controller -> Service -> DAO -> DB
	- Servlet

## 진행 과정

1. 클라이언트가 Url을 요청하면 웹 브라우저에서 스프링으로 request가 보내진다.
2. Dispatcher Servlet이 request를 받으면 Handler Mapping을 통해 해당 url을 담당하는 Controller를 탐색 후 찾아낸다.
3. 찾아낸 Controller로 request를 보내주고 보내주기 위해 필요한 Model을 구성한다.
4. Model에서는 페이지 처리에 필요한 정보들을 Database에 접근하여 쿼리문을 통해 가져온다.
5. 데이터를 통해 얻은 Model 정보를 Controller에게 response해주면 Controller는 이를 받아 Model을 완성시켜 Dispatcher Servlet에게 전달해준다.
6. Dispatcher Servlet은 View Resolver를 통해 request에 해당하는 view 파일을 탐색 후 받아낸다.
7. 받아낸 View 페이지 파일에 Model을 보낸 후 클라이언트에게 보낼 페이지를 완성시켜 받아낸다.
8. 완성된 View 파일을 클라이언트에 response하여 화면에 출력한다.

## 구성 요소

1. Dispatcher Servlet
	- 모든 request를 처리하는 중심 컨트롤러.
	- Servlet Container에서 Http 프로토콜을 통해 들어오는 모든 request에 대해 제일 앞단에서 중앙집중식으로 처리해주는 핵심적인 역할을 한다.
	- Controller에게 클라이언트의 요청을 전달하고 Controller가 리턴한 결과값을 view에게 전달하여 알맞은 응답을 생성한다.
2. Handler Mapping
	- 클라이언트의 request Url을 어떤 컨트롤러가 처리해야 할 지 찾아서 Dispatcher Servlet에게 전달해주는 역할을 담당한다.
	- 컨트롤러 상에서 url을 매핑하기 위해 `@RequestMapping`을 사용하는데 핸들러가 이를 찾아주는 역할을 한다.
3. Controller
	- 실질적인 요청을 처리하는 곳
	- 모델의 처리 결과를 담아 Dispatcher Servlet에게 반환해준다.
4. ModelAndView
	- 컨트롤러가 처리한 데이터 및 화면에 대한 정보를 보유한 객체
5. ViewResolver
	- 컨트롤러의 처리 결과를 만들 View를 결정해주는 역할을 담당한다.
6. View
	- 컨트롤러의 처리 결과를 보여줄 응답화면을 생성한다.


---

참조

https://gmlwjd9405.github.io/2018/12/20/spring-mvc-framework.html

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/Spring/Spring%20MVC.md

https://seco-log.tistory.com/86
