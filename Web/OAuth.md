# OAuth

> **Open Authentification**
> 인터넷 사용자들이 비밀번호를 제공하지 않고 다른 웹사이트 상의 자신들의 정보에 대해 웹사이트나 애플리케이션의 접근 권한을 부여할 수 있는 공통적인 수단으로서 사용되는, 접근 위임을 위한 개방형 표준이다.

이러한 매커니즘은 Google, Facebook, Twitter 등에서 사용되고 있다. 

이러한 외부 소셜 계정을 기반으로 간편히 회원가입 및 로그인할 수 있으며 연동되는 외부 웹 어플리케이션에서 외부 플랫폼이 제공하는 기능을 사용할 수 있다. 

이 때 사용되는 프로토콜이 바로 **OAuth**이다.

<br />

## OAuth 구성 요소

| 구분 | 설명 |
|-------|------|
| Resource Owner | 웹 서비스를 이용하려는 유저, 자원(개인정보)을 소유하는 자, 사용자 |
| Client | 자사 또는 개인이 만든 애플리케이션 서버 |
| Authorization Server | 권한을 부여(인증에 사용할 아이템을 제공)해주는 서버 |
| Resource Server | 사용자의 개인정보를 가지고 있는 애플리케이션 (Google, Facebook, Twitter 등) 회사 서버 |
| Access Token | 자원에 대한 접근 권한을 Resource Owner가 인가하였음을 나타내는 자격증명 |
| Refresh Token | Client는 Authorization Server로부터 Access Token(비교적 짧은 만료기간을 가짐)과 Refresh Token(비교적 긴 만료기간을 가짐)을 함께 부여 받는다. Access Token은 보안상 만료 기간이 짧기 때문에 얼마 지나지 않아 만료되면 사용자는 로그인을 다시 시도해야한다. 그러나 Refresh Token이 있다면 만료되더라도 다시 Access Token을 재발급 받아 재 로그인할 필요없게끔 한다. |

<br />

## 인증 과정

> 소비자 <-> 서비스 제공자

1.  소비자가 서비스 제공자에게 요청토큰을 요청한다.
2.  서비스 제공자가 소비자에게 요청토큰을 발급해준다.
3.  소비자가 사용자를 서비스제공자로 이동시킨다. 여기서 사용자 인증이 수행된다.
4.  서비스 제공자가 사용자를 소비자로 이동시킨다.
5.  소비자가 접근토큰을 요청한다.
6.  서비스제공자가 접근토큰을 발급한다.
7.  발급된 접근토큰을 이용해서 소비자에서 사용자 정보에 접근한다.

<br />

---

참조

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/OAuth.md

https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-OAuth-20-%EA%B0%9C%EB%85%90-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC

