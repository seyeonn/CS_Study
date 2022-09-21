# Vue CLI + Spring Boot 연동하여 환경 구축하기

![vuespring](https://user-images.githubusercontent.com/38287375/191895426-ae62478d-d8c9-4736-a02f-6a5a69628f0a.png)

> frontend -> Vue.js
> backend -> Spring Boot
>
> Spring에서 컨트롤러를 통해 DB 관리나 데이터에 관한 비즈니스 로직을 잘 처리하고 이에 대한 값을 활용해 Vue에서 화면으로 보여줄 템플릿을 만들어나가는 방식

### 프로젝트 구성

1. Spring Boot Project

먼저, 스프링 부트 프로젝트를 만든다. ( Spring Boot 프로젝트 안에 Vue 프로젝트 연동)

2. Vue.js Project

Vue CLI를 이용하여 프로젝트를 생성한다.

Vue CLI는 Vue.js 개발을 위한 시스템으로 Vue.js Core에서 공식적으로 제공하는 CLI이다. 개발에 집중할 수 있도록 프로젝트 구성을 빠르고 쉽게 도와주는 역할을 하고 있다.

Node.js를 설치한 상태라면 npm을 통해 터미널에서 Vue CLI 설치가 가능하다.

```
$ npm i -g @vue/cli
$ npm i -g @vue/cli-init
```

몇가지 설정하는 부분이 나온다.

  

> Project name
> 
> Project description
> 
> Author

  

이 3가지는 자신의 프로젝트에 맞게 작성해주면 된다.

> Vue build는 standalone
> 
> vue-router는 설치(Yes)
> 
> Use ESLint to lint your code도 Yes
> 
> ESLint preset은 Standard

  

그 이후 test부분은 진행할 사람들은 Yes, 안할사람은 No로 넘어가면 된다.

터미널 창에서 열심히 파일들이 다운로드되는 모습을 볼 수 있다. (시간 조금 걸림)

  

끝나면 스프링부트 루트 폴더에 'frontend'라는 Vue 프로젝트 폴더가 생성된 모습을 확인할 수 있다.

#### Webpack 번들링 output 설정

  

Vue에서 작성한 코드들을 번들링하고, 이 결과를 어느 위치에서 뽑아낼 지 정해야 한다.

  

Spring Boot에서는 자동설정으로 src/main/resources에 번들링한 결과들을 저장하도록 되어있다.

(이곳에 index.html과 정적 파일(css, img, javascript)들이 인식됨)

  

이 구역에 잘 번들링 될 수 있도록, Vue 프로젝트에서 경로 지정을 해주자.

config/index.js을 열어 build 부분에 정의한 곳을 수정해야 한다.

해당 위치에 절대 경로로 위와 같이 수정해준다.

이제 터미널에서 'npm run build' 커맨드를 입력하여 빌드를 실행한다.

이제 Spring Boot의 src/main/resources/static 경로에 들어가보면, 번들링 된 정적 파일들이 생성된 모습을 확인할 수 있다.

그렇지만 아직 스프링 부트에서 데이터베이스 설정 및 그에 맞는 드라이버 라이브러리 설치와 jdbc 설정이 아직 안되어 있기 때문에 에러가 발생할 것이다.

현재는 어떤 데이터베이스를 지정할 지 결정이 되있는 상태가 아니기 때문에 스프링 부트의 메인 클래스에서 어노테이션을 추가해주자.

```
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;
import org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration;

@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})
```

이제 다시 스프링 부트 메인 애플리케이션을 실행하면 디버깅 창에서 에러가 없어진 걸 확인할 수 있다.

이제 localhost:8080/으로 접속하면, Vue에서 만든 화면이 잘 나오는 것을 확인할 수 있다.

---

참조

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/Vue/Vue%20CLI%20%2B%20Spring%20Boot%20%EC%97%B0%EB%8F%99%ED%95%98%EC%97%AC%20%ED%99%98%EA%B2%BD%20%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0.md