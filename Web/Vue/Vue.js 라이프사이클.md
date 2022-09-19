# Vue.js 라이프사이클

> **라이프사이클(Lifecycle)**
> 어떤 Vue 인스턴스나 컴포넌트가 생성될 때 미리 사전에 정의된 몇 단계의 과정을 거치게 되는데 이를 라이프사이클이라 한다.
> 즉, Vue 인스턴스가 생성된 후 우리 눈에 보여지고 사라지기까지의 단계를 일컫는 말이다.


![vue](https://user-images.githubusercontent.com/38287375/191433425-00ee00b2-88da-49e9-b97d-1e6b686f1fde.png)

Vue.js 라이프사이클은 크게 4가지로 구성된다.

- Creation (생성)
- Mounting (부착)
- Updating (업데이트)
- Destruction (제거)

<br />

## Creation

**컴포넌트 초기화 단계**

Creation 단계에서 실행되는 훅(hook)들이 라이프사이클 중 가장 먼저 실행된다.

아직 컴포넌트가 DOM에 추가되기 전으로 서버 렌더링에서도 지원된다.

클라이언트와 서버 렌더링 모두에서 처리해야 할 일이 있다면 이 단계에 적용하면 된다.

- beforeCreate
  > 가장 먼저 실행되는 훅
  > 아직 데이터나 이벤트가 셋팅되지 않은 시점이므로 접근 불가능
- created
  > 데이터, 이벤트(computed, methods, watch)가 활성화되어 접근이 가능함
  > 하지만 아직 템플릿과 virtual DOM은 마운트 및 렌더링 되지 않은 상태임

<br />

## Mounting

**DOM 삽입 단계**

초기 렌더링 직전 컴포넌트에 직접 접근이 가능하다.

컴포넌트 초기에 셋팅되어야할 데이터들은 created에서 사용하는 것이 낫다.

- beforeMount
   > 템플릿이나 렌더 함수들이 컴파일된 후에 첫 렌더링이 일어나기 직전에 실행됨
   > 많이 사용하지 않음
- mounted
   > 컴포넌트, 템플릿, 렌더링된 DOM에 접근이 가능함
   > 모든 화면이 렌더링된 후에 실행
   > 일반적으로 가장 많이 사용

주의할 점

부모와 자식 관계의 컴포넌트에서 생각한 순서대로 mounted가 발생하지 않는다. 즉, 부모의 mounted가 자식의 mounted보다 먼저 실행되지 않음 (부모는 자식의 mounted 훅이 끝날 때까지 기다림)

<br />

## Updating

**렌더링 단계**

컴포넌트에서 사용되는 반응형 속성들이 변경되거나 다시 렌더링되면 실행된다.

디버깅을 위해 컴포넌트가 다시 렌더링되는 시점을 알고 싶을 때 사용이 가능하다.

- beforeUpdate
   > 컴포넌트의 데이터가 수정되어 업데이트 사이클이 시작될 때 실행됨
   > 돔이 다시 렌더링되고 패치되기 직전의 상태
- updated
   > 컴포넌트의 데이터가 수정되어 다시 렌더링된 이후에 실행됨
   > 업데이트가 완료된 상태이므로 DOM 종속적인 연산이 가능함

<br />

## Destruction

**해체 단계**

- beforeDestroy
   > 해체되기 직전에 호출됨
   > 이벤트 리스너를 제거하거나 reactive subscription을 제거하고자 할 때 유용함
- destroyed
   > 해체된 이후에 호출됨
   > Vue 인스턴스의 모든 디렉티브가 바인딩 해제되고 모든 이벤트 리스너가 제거됨

<br />

---

참조

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/Vue/Vue.js%20%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4%20%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0.md

https://velog.io/@yeyo0x0/Vue.js-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%ED%9B%85
