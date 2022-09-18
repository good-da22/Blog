## 서브 쿼리 (Sub Query)

<br>

서브 쿼리(sub query)란 다른 쿼리 내부에 포함되어 있는 SELECT문을 의미

서브 쿼리를 포함하고 있는 쿼리를 외부 쿼리(outer query) 또는 메인 쿼리(main query)라고 부르며, 서브 쿼리는 내부 쿼리(inner query)라고도 부른다.

서브 쿼리는 비교 연산자의 오른쪽에 기술해야 하고 반드시 괄호 () 로 감싸져 있어야 한다.

서브 쿼리를 모른다면 JOIN을 사용해야 한다.

JOIN의 경우 쿼리가 복잡해지거나 카테시안곱으로 인한 속도 저하 발생 가능(case by case)

서브 쿼리를 이용하여 CREATE, INSERT, UPDATEm DELETE 가능

<br>

### 서브 쿼리 종류

<br>

- 중첩 서브 쿼리(Nested Subquery) : WHERE 문에 작성하는 서브 쿼리
  - 단일 행
  - 복수(다중) 행
  - 다중 컬럼

- 인라인 뷰(Inline View) : FROM 문에 작성하는 서브 쿼리
  
- 스칼라 서브 쿼리(Scalar Subquery) : SELECT 문에 작성하는 서브 쿼리

<br>

### 주의사항

<br>

서브 쿼리는 반디시 ()로 감싸야 하낟.

서브 쿼리는 단일 행 또는 다중 행 비교 연산자와 함께 사용된다.

**서브 쿼리가 사용 가능한 곳**
- SELECT
- FROM
- WHERE
- HAVING
- ORDER BY
- INSERT문의 VALUES
- UPDATE문의 SET

<br>

### Nested Subquery

<br>

WHERE 문에 작성하는 서브 쿼리

- Nested Subquery - 단일 행

    서브 쿼리의 결과가 단일행을 리턴

- Nested Subquery - 다중 행

    서브 쿼리의 결과 다중행을 리턴

    IN, ANY, ALL

- Nested Subquery - 다중 열

    서브 쿼리의 결과가 다중 열을 리턴

<br>

### Inline View

<br>

FROM 절에 사용되는 서브 쿼리

서브 쿼리가 FROM 절에 사용되면 뷰(View) 처럼 결과가 동적으로 생성된 테이블로 사용 가능

임시적인 뷰이기 때문에 데이터베이스에는 저장되지 않는다.

동적으로 생성된 테이블이기 때문에 column을 자유롭게 참조 가능

<br>

### Scalar Subquery

<br>

SELECT 절에 사용되는 서브 쿼리

한 개의 행만 반환