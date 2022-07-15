# REST API

> **REST API(Representational State Transfer API)란**
> REST를 기반으로 만들어진 API를 의미한다. 

<br />

## REST

**REST(Representational State Transfer)** 의 약자로 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것을 의미한다.

즉 REST란
1. HTTP URI를 통해 자원을 명시하고,
2. HTTP Method(POST, GET, PUT, DELET)를 통해
3. 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미한다.

-> 웹(HTTP)의 장점을 활용한 아키텍쳐

<br />

### REST의 구성 요소

1. Resource (자원)
	- http://myweb/users 와 같은 URI
	- 모든 것을 Resource (명사)로 표현하고, 세부 Resource에는 id를 붙인다. 

2. Method (자원에 대한 행위)
	| Method | 의미 | Idempotent |
	|------|------|------|
	| POST | Create | No |
	| GET | Select | Yes |
	| PUT | Update | Yes |
	| DELETE | Delete | Yes |

3. Message (자원에 대한 행위의 내용)
	- 메세지 포맷이 존재 : JSON, XML과 같은 형태가 있다. 
	    ```
	    HTTP POST, http://myweb/users/
	    {
	    	"users" : {
	    		"name" : "terry"
	    	}
	    }
	    
	    ```

<br />

### REST의 특징

1. Server-Client (서버 클라이언트 구조)
2. Stateless (무상태)
3. Cacheable (캐시 처리 가능)
4. Layered System (계층화)
5. Uniform Interface (인터페이스 일관성)

<br />

## REST API 규칙

1. URI는 동사보다는 명사를, 대문자보다는 소문자를 사용해야 한다.
2. 마지막에 슬래시(/)를 포함하지 않는다.
3. 언더바)(_) 대신 하이픈(-)을 사용한다.
4. 파일확장자는 URI에 포함하지 않는다.
5. 행위를 포함하지 않는다.

<br />

## RESTful

RESTful이란 REST의 원리를 따르는 시스템을 의미한다.
하지만 REST를 사용했다 하여 모두가 RESTful한 것은 아니다. 

REST API의 설계 규칙을 올바르게 지킨 시스템을 RESTful하다 말할 수 있으며 모든 CRUD 기능을 POST로 처리 하는 API 혹은 URI 규칙을 올바르게 지키지 않은 API는 REST API를 사용하였지만 RESTful하지 못한 시스템이라고 할 수 있다.

<br />

---
참조

https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/%5BWeb%5D%20REST%20API.md

