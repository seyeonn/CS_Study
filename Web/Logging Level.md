# Logging Level


> **로그(Log)란**
> 프로그램 개발이나 운영 시 발생하는 문제점을 추적하거나 운영 상태를 모니터링하기 위한 텍스트이다.
>
> `System.out.println();` 를 사용하여 로그를 확인할 수 있지만 이보다 로그를 기록하는 클래스를 만들어 사용하는 것이 더 좋은 방법이다.

## Log4j

**Log4j**는 Java/Kotlin/Scala/Groovy/Clojure **코딩 도중에 프로그램의 로그를 기록해주는 라이브러리**로, 이클립스, 인텔리제이, 안드로이드 스튜디오 등에 추가해서 프로그램 실행 시 자동으로 지정한 경로에 로그를 저장해주는 기능을 한다.


### 레벨
```
TRACE > DEBUG > INFO > WARN > ERROR > FATAL

* INFO로 셋팅하면 INFO, WARN, ERROR, FATAL은 기록된다.
* TRACE로 설정하면 모든 레벨의 로그가 전부 기록되지만 FATAL로 설정하면 FATAL보다 하위 수준의 로그는 기록되지 않는다.
```

- FATAL : 아주 심각한 에러가 발생한 상태를 나타낸다.
- ERROR : 어떠한 요청을 처리하는 중 문제가 발생한 상태를 나타낸다.
- WARN : 프로그램의 실행에는 문제가 없지만, 향후 시스템 에러의 원인이 될 수 있는 경고성 메세지를 나타낸다.
- INFO : 어떠한 상태 변경과 같은 정보성 메세지를 나타낸다.
- DEBUG : 개발 시 디버그 용도로 사용하는 메세지를 나타낸다.
- TRACE : 디버그 레벨이 너무 광범위한 것을 해결하기 위해서 좀 더 상세한 이벤트를 나타낸다.

<br />

## Log4j 취약점

2021년, 간단한 문자열을 활용해 원격 코드 실행을 통한 서버 장악이 가능하다는 취약점이 발견되었다. 

이 이슈가 문제가 되는 것은 서버에 로그인한 것 만으로 해커가 사용자의 컴퓨터를 사실상 원격 조종할 수 있는 것이기 때문이다.

## Log4j 조치 방법

이 문제는 Log4j 버전 2.0-beta-9 부터 2.14.1 사이를 사용하는 경우에 해당 된다. 

1. 관련 문제가 해결된 버전으로 업그레이드 하는 방식 
	> but, 단독으로 동작하는 라이브러리가 아니라 자바 기반의 큰 프로젝트 안에 포함되는 로깅용 라이브러리 이기 때문에 버전만 업그레이드 할 경우 전체 프로젝트 빌드 과정에서 에러가 발생할 수 있다. 따라서 이 방법의 경우, 일부 에러가 발생하는 부분의 코드 수정이 필요하다.

2. 현재 사용중인 log4j jar 파일 안에 있는 JndiLookup.class 파일을 삭제하는 방안
	> `
zip -q -d log4j-core-*.jar org/apache/logging/log4j/core/lookup/JndiLookup.class
`
위와 같이 삭제를 실행할 수 있는데 이후 JndiLookup 기능은 동작이 불가능하다. 이 방법으로 조치한 경우 로그에 WARN이 발생하기도 했다. (Hive 경우)

3. 사용중인 Log4j의 버전이 2.10 ~ 2.14.1까지의 경우에만 적용이 가능한 방안 - 설정 파일에 아래의 설정 두가지 중 하나를 넣어주는 방안
	> `
log4j2.formatMsgNoLookups=true
`
or
`
LOG4J_FORMAT_MSG_NO_LOOKUPS=true
`
 

---

참조

https://yunyoung1819.tistory.com/30

https://devocean.sk.com/blog/techBoardDetail.do?ID=163523





