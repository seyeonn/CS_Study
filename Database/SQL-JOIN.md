# [Database SQL] JOIN

> **조인(JOIN)**
> 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 방법

테이블을 연결하려면 적어도 하나의 컬럼을 서로 공유하고 있어야 하므로 이를 이요하여 데이터 검색에 활용한다.

### JOIN 종류

- INNER JOIN
- LEFT OUTER JOIN
- RIGHT OUTER JOIN
- FULL OUTER JOIN
- CROSS JOIN
- SELF JOIN

<br />

## INNER JOIN

![inner join](https://user-images.githubusercontent.com/38287375/193407887-061b171f-9bb1-490e-a931-3e99945b6af7.png)

교집합으로 기준 테이블과 조인하는 테이블의 중복된 값을 보여준다.

```sql
SELECT
A.NAME, B.AGE
FROM EX_TABLE A
INNER JOIN JOIN_TABLE B ON A.NO_EMP = B.NO_EMP
```

<br />

## LEFT OUTER JOIN

![left outer join](https://user-images.githubusercontent.com/38287375/193407985-6dfff98f-d2ec-49f7-bbd6-59abb9598371.png)

기준 테이블 값과 조인 테이블과 중복된 값을 보여준다.
왼쪽 테이블을 기준으로 JOIN 한다고 생각하면 된다.

```sql
SELECT
A.NAME, B.AGE
FROM EX_TABLE A
LEFT OUTER JOIN JOIN_TABLE B ON A.NO_EMP = B.NO_EMP
```

<br />

## RIGHT OUTER JOIN

![right outer join](https://user-images.githubusercontent.com/38287375/193408049-c582c252-65c4-4b19-b915-fd3f77781cb4.png)

LEFT OUTER JOIN과는 반대로 오른쪽 테이블 기준으로 JOIN하는 것이다.

```sql
SELECT
A.NAME, B.AGE
FROM EX_TABLE A
RIGHT OUTER JOIN JOIN_TABLE B ON A.NO_EMP = B.NO_EMP
```

<br />

## FULL OUTER JOIN

![full outer join](https://user-images.githubusercontent.com/38287375/193408084-c7191855-43ea-49e2-b457-063cac3d0e8e.png)

합집합을 말한다. A와 B 테이블의 모든 데이터가 검색된다.

```sql
SELECT
A.NAME, B.AGE
FROM EX_TABLE A
FULL OUTER JOIN JOIN_TABLE B ON A.NO_EMP = B.NO_EMP
```

<br />

## CROSS JOIN

![cross join](https://user-images.githubusercontent.com/38287375/193408127-a9768007-7613-4c8e-860f-6e7244b5ad4e.png)

모든 경우의 수를 전부 표현해주는 방식이다.
A가 3개, B가 4개면 총 3*4 = 12개의 데이터가 검색된다.

```sql
SELECT
A.NAME, B.AGE
FROM EX_TABLE A
CROSS JOIN JOIN_TABLE B
```

<br />

## SELF JOIN

![self join](https://user-images.githubusercontent.com/38287375/193408164-84431788-41db-47d4-b8c1-a123efa43eed.png)

자기자신과 자기자신을 조인하는 것이다.
하나의 테이블을 여러번 복사해서 조인한다고 생각하면 된다.
자신이 갖고 있는 컬럼을 다양하게 변형시켜 활용할 때 자주 사용한다.

```sql
SELECT
A.NAME, B.AGE
FROM EX_TABLE A, EX_TABLE B
```

<br />

---

참조

https://coding-factory.tistory.com/87

