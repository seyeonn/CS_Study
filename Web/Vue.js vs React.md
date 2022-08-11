# Vue.js vs React

## 프레임워크 vs UI 라이브러리

> 프레임워크 -> Vue.js
> 라이브러리 -> React

### 프레임워크

- 뷰는 **자바스크립트 프레임워크**이다. 
- 부분적인 사용이 불가능하고 프레임워크 안으로 들어가서 프레임워크가 지원해주는 문법에 따라 작성해야 한다.
- 그렇기 때문에 라이브러리와 달리 더 많은 기능을 디폴트로 제공해준다.


### 라이브러리

- 라이브러리는 참고가 용이하고 라이브러리의 일부부만 가져와서 사용하는 게 편리하다는 장점이 있다.
- 리액트는 UI라이브러리이기 때문에 리액트 자체로는 전역 상태 관리, 라우팅, 빌드 시스템 등을 지원하지 않는다. 
- 그렇기 때문에 리액트는 별도의 라이브러리를 통해 Redux, Recoil, React-router-dom 등을 사용해야 한다.
- 사용자가 필요할 때 가져다 쓰고 빼며 부분적으로 사용이 가능하다.

<br />

## 코드 형태의 차이

### Vue의 코드

- JTML, JS, CSS 코드 영역을 분리해서 작성한다.
- `.vue` 파일을 만들 때에도 패턴이 존재한다.
- `.vue`에서 <template>에 HTML 작성 영역, <script> 안에는 JS, <style> 안에는 CSS를 작성한다.

### React의 코드

- JSX(JavaScript XML) 형태로 코드를 작성하여 JavaScript 문법을 응용하기 때문에 JavaScript 만으로 UI 로직과 DOM을 구현한다.


### 둘의 차이

- 리액트는 뷰에 비해 자유롭게 JS를 통해 구현하지만 뷰는 뷰에서 제공해주는 방법을 반드시 사용해야 한다.

<br />

## 컴포넌트 분리와 재사용

### Vue
- 뷰는 새로운 컴포넌트를 만들어 분리하기 위해서 새로운 파일을 하나 더 만들고, 그에 따라 하나의 파일에 해당하는 template, script, style을 모두 작성해야 한다.
- 뿐만 아니라 props를 전달하는 과정에서도 해당 컴포넌트를 사용하는 모든 파일을 오가며 작성해주어야 한다.

### React
- 리액트의 가장 큰 장점 중 하나는 컴포넌트의 생성 및 재사용성이다.
- 파일별로 컴포넌트를 분리할 수 있으며 새로운 함수형 컴포넌트를 생성하고, props 형태로 전달하거나 또는 다른 곳에서 재사용하는 것이 매우 용이하다.

<br />

## 개발 CLI

> CLI (Command Line Interface)
> 명령어 인터페이스
> 텍스트 터미널을 통해 사용자와 컴퓨터가 상호 작용하는 방식

- Vue.js -> vue-cli
- React -> create-react-app

<br />

## 데이터 변이

- Vue.js : 반드시 데이터 객체를 생성한 이후 data를 업데이트 할 수 있음 (data 업데이트 시마다 setState 알아서 결합함.)
```
this.name = 'lee';
```

- React : state 객체를 만들고, 업데이트에 조금 더 작업이 필요
```
this.setState({name: 'lee'})
```

<br />

---

참조

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/Vue.js%EC%99%80%20React%EC%9D%98%20%EC%B0%A8%EC%9D%B4.md

https://nyol.tistory.com/148



