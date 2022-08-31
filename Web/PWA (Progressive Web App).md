# PWA (Progressive Web App)

PWA는 HTML, CSS, JavaScript와 같은 웹 기술로 만드는 앱이다. 하지만 그 느낌과 기능은 실제 네이티브 앱과 견줄 수 있을 정도로 좋아야 한다.

즉, 웹에서 사용하는 기술과 네이티브 앱의 장점을 결합한 것이다.

<br />

## 네이티브 앱과 PWA의 차이

네이티브 앱은 일반적으로 해당 플랫폼에 특화된 프로그래밍 언어로 만드는 경우가 많다. 즉, iOS의 앱은 Swift로, Android의 앱은 Java나 Kotlin으로 만드는 식이다. 

PWA는 일단 홈 화면에 저장되면 브라우저에서 실행되며 네이티브 앱처럼 동작한다. 그리고 보안상의 이유로 브라우저가 접근하지 못하는 시스템 하드웨어와 소프트웨어에도 접근할 수 있다. 따라서 PWA의 성능이 뛰어나다면 사용자들은 자신들이 웹 기반의 앱을 사용하고 있는 것인지 아니면 네이티브 앱을 사용하고 있는 것인지 구분하기 힘들다.

<br />

## PWA의 장점

- 다양한 앱스토어에 출시하기 위해서 별도의 프로세스를 거치지 않아도 된다.
- 일반적인 웹 기술을 활용해서 PWA를 만들 수 있다.
- 기존의 웹 사이트를 앱으로 만들 수 있기 때문에 추가로 유지관리해야 하는 코드 베이스가 적다.
- PWA는 기본적으로 반응형이기 때문에 다양한 화면 크기에도 잘 동작한다.
- PWA는 검직엔진을 통해서 찾을 수 있다.

<br />

## PWA의 주요 구성요소

- 보안 연결(HTTPS) : PWA는 신뢰할 수 있는 연결 상태에서만 동작하기 때문에 보안 연결을 통해서 서비스를 제공해야 한다. 이건 단지 보안상의 이유 때문만은 아니고, 사용자들의 신뢰를 얻기 위해서도 아주 중요한 부분이다.
- 서비스 작업자(Service Worker) : 서비스 작업자는 백그라운드에서 실행되는 스크립트이다. 서비스 작업자는 네트워크와 관련된 요청의 처리를 도와주기 때문에 여러분은 그 점에 대해서는 걱정하지 않고 더욱 복잡한 작업을 수행할 수 있다.
- 매니페스트 파일(Manifest File) : 이것은 JSON 파일이며, PWA가 표시되고 기능하는 방식에 대한 정보들이 포함되어 있는 것이다. 여기에서는 PWA의 이름, 설명, 아이콘, 색상 등을 지정할 수 있다.

<br />

## PWA 제공 기능

- 프로그레시브 : 점진적 개선을 통해 작성돼서 어떤 브라우저든 상관없이 모든 사용자에게 적합
- 반응형 : 데스크톱, 모바일, 테블릿 등 모든 폼 factor에 맞음
- 연결 독립적 : 서비스 워커를 사용해 오프라인에서도 작동이 가능함
- 안전 : HTTPS를 통해 제공이 되므로 스누핑이 차단되어 콘텐츠가 변조되지 않음
- 검색 가능 : W3C 매니페스트 및 서비스 워커 등록 범위 덕분에 '앱'으로 식별되어 검색이 가능함
- 재참여 가능 : 푸시 알림과 같은 기능을 통해 쉽게 재참여가 가능함

<br />

---

참조

https://blog.wishket.com/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%A0%88%EC%8B%9C%EB%B8%8C-%EC%9B%B9-%EC%95%B1pwa%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%99%9C-%ED%95%84%EC%9A%94%ED%95%9C%EA%B0%80/

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/PWA%20(Progressive%20Web%20App).md
