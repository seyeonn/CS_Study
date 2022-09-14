# Spring Security - Authentication and Authorization

> API에 권한 기능이 없으면, 아무나 회원 정보를 조회하고 수정하고 삭제할 수 있다. 따라서 이를 막기 위해 인증된 유저만 API를 사용할 수 있도록 해야하는데, 이때 사용할 수 있는 해결 책 중 하나가 Spring Security다.

## 인증처리 과정

![spring security](https://user-images.githubusercontent.com/38287375/190910986-f10d1e35-8fb3-4624-a7ea-45b9a3c617b4.png)

1) 처음에 요청이 들어오면 AuthenticationFilter(UsernamePassAuthenticationFilter)를 거친다.  
  
2) 요청에 따른 UsernamePasswordAuthenticationToken을 생성한다. (Authentication 인터페이스의 구현체다.)  
  
3) UsernamePasswordAuthenticationToken(통상 Token이라고 하겠다.)을 AuthenticationManager에게 이 Token은 올바른 유저인지 물어본다.  
  
4) AuthenticationManager는 1개 이상의 AuthenticationProvider(통상 A-Provider)를 갖고 있는데, A-Provider는 Token 객체를 적절히 판단하여 인증처리를 할려고 한다.  
  
5) A-Provider가 우리가 직접 구현한 서비스(UserDetailsService 구현 클래스)에 해당 유저에게 인증요청을 보내 사용자 정보를 가져온다.  
  
6) UserDetailsService 구현 클래스는 사용자 정보를 가져와 UserDetails를 반환한다.  
  
7~10) Provider는 UserDetailsService에서 반환된 UserDetails와 클라이언트가 제공한 인증정보(Token)를 대조해서 이용자가 정당한 사용권한을 가지고 있는지 확인한다.  
그리고 SecurityContext에 저장한다.

<img width="898" alt="spring security2" src="https://user-images.githubusercontent.com/38287375/190911068-9b2ffdeb-ec5e-409f-847f-9566fbbc3c88.png">

## 주요 객체

1. AuthenticationManager
    
    > 인증요청을 받고 Authentication를 채운다.  
    > 유저의 requet 담긴 Authentication를 AuthenticationManager에 넘겨주고, AuthenticationManager를 구현한  
    > ProviderManager가 처리한다. 정확히는 ProviderManager는 private List provider; 로 여러 AuthenticationProvider를 가질 수 있는데, 이것들이 처리를 해서 Authentication를 반환해 준다.(실패하면 예외를 던짐)

2. AuthticationProvider
    
    > 실제 인증이 일어나며, 성공하면 Authentication.isAuthenticated = true를 한다.
    

3. Authentication
    
    > 모든 접근 주체(=유저) 는 Authentication 를 생성한다. 이것은 SecurityContext 에 보관되고 사용된다.  
    > 즉, security의 세션들은 내부 메모리(SecurityContextHolder)에 쌓고 꺼내쓰는 것이다.  
    > Authentication 인터페이스를 상속받는 UserDetails 인터페이스가 중요한 이유이다.

## Spring Security Filter

![spring security3](https://user-images.githubusercontent.com/38287375/190911191-6bb0aaeb-d91e-4cbf-8e05-d6f3f30bf635.png)

Filter의 종류는 상당히 많다. 위에서 예시로 든 클라이언트가 리소스에 대한 접근 권한이 없을 때 처리를 담당하는 필터는  `UsernamePasswordAuthenticationFilter`다.

인증 권한이 없을 때 오류를 JSON으로 내려주기 위해 해당 필터가 실행되기 전 처리가 필요할 것이다.

  

API 인증 및 권한 부여를 위한 작업 순서는 아래와 같이 구성할 수 있다.

1.  회원 가입, 로그인 API 구현
2.  리소스 접근 가능한 ROLE_USER 권한을 가입 회원에게 부여
3.  Spring Security 설정에서 ROLE_USER 권한을 가지면 접근 가능하도록 세팅
4.  권한이 있는 회원이 로그인 성공하면 리소스 접근 가능한 JWT 토큰 발급
5.  해당 회원은 권한이 필요한 API 접근 시 JWT 보안 토큰을 사용

  

이처럼 접근 제한이 필요한 API에는 보안 토큰을 통해서 이 유저가 권한이 있는지 여부를 Spring Security를 통해 체크하고 리소스를 요청할 수 있도록 구성할 수 있다.

---

참조

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/Spring/Spring%20Security%20-%20Authentication%20and%20Authorization.md

https://velog.io/@mooh2jj/Security-%EC%9D%B8%EC%A6%9D%EC%9D%B8%EA%B0%80%EC%B2%98%EB%A6%AC

