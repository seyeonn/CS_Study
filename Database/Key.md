# Key

> **키(Key)**
> 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 속성(Attribute)이다.
>
> 튜플(tuple) : 릴레이션을 구성하는 각각의 행, 속성의 모임으로 구성된다. 파일 구조에서는 레코드와 같은 개념 ( 튜플의 수 = 카디널리티 = 기수 = 대응수 )

<br />

## 후보키 (Candidate Key)

- 릴레이션을 구성하는 속성들 중에서 튜플을 **유일하게 식별할 수 있는 속성들의 부분집합**을 의미한다.
- **모든 릴레이션은 반드시 하나 이상의 후보키를 가져야**한다.
- 릴레이션에 있는 모든 튜플에 대해서 **유일성과 최소성을 만족**시켜야 한다.
	- 유일성 : Key로 하나의 Tuple을 유일하게 식별할 수 있음
	- 최소성 : 꼭 필요한 속성으로만 구성

<br />

## 기본키 (Primary Key)

- 후보키 중에서 선택한 주가 되는 키 (Main Key)
- 한 릴레이션에서 **특정 튜플을 유일하게 구별할 수 있는 속성**
- **Null 값을 가질 수 없다. ** (개체 무결성의 첫번째 조건)
- 기본키로 정의된 속성에는 **동일한 값이 중복되어 저장될 수 없다.** (개체 무결성의 두번째 조건)

<br />

## 대체키 (Alternate Key)

- **후보키가 둘 이상일 때 기본키를 제외한 나머지 후보키들을 말한다.**
- 보조키라고도 한다.

<br />

## 슈퍼키 (Super Key)

- **슈퍼키는 한 릴레이션 내에 있는 속성들의 집합으로 구성된 키**로서 릴레이션을 구성하는 모든 튜플 중 슈퍼키로 구성된 속성의 집합과 동일한 값은 나타내지 않는다.
- 릴레이션을 구성하는 모든 튜플에 대해 **유일성은 만족하지만 최소성은 만족시키지 못한다.**

<br />

## 외래키 (Foreign Key)

- 관게(Relation)를 맺고 있는 릴레이션 R1, R2에서 릴레이션 R1이 참조하고 있는 릴레이션 R2의 기본키와 같은 R1 릴레이션의 속성
- 외래키는 **참조되는 릴레이션의 기본키와 대응되어 릴레이션 간에 참조 관계를 표현하는데 중요한 도구**로 사용된다.
- **외래키로 지정되면 참조 테이블의 기본키에 없는 값은 입력할 수 없다.** (참조 무결성 조건)

<br />

---

참조

https://limkydev.tistory.com/108
 