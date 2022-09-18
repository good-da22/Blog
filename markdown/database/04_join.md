## JOIN

<br>

둘 이상의 테이블에서 데이터가 필요한 경우 테이블 JOIN이 필요

일반적으로 JOIN 조건을 포함하는 WHERE 절을 작성해야 한다.

JOIN 조건은 일반적으로 각 테이블의 PK와 FK로 구성

<br>

### JOIN 종류

<br>

- INNER JOIN
- OUTER JOIN
  - LEFT OUTER JOIN
  - RIGHT OUTER JOIN

<br>

### JOIN 조건의 명시에 따른 구분

<br>

- NATURAL JOIN
- CROSS JOIN(FULL JOIN, CARTESIAN JOIN)

<br>

### JOIN 주의

<br>

JOIN의 처리는 어느 테이블을 먼저 읽을지를 결정하는 것이 중요(처리할 작업량이 상당히 달라진다)

INNER JOIN : 어느 테이블을 먼저 읽어도 결과가 달라지지 않아 MySQL 옵티마이저가 JOIN의 순서를 조절해 다양한 방법으로 최적화 수행

OUTER JOIN : 반드시 OUTER가 되는 테이블을 먼저 읽어야 하므로 옵티마이저가 JOIN 순서를 선택할 수 없다.

<br>

### INNER JOIN

<br>

가장 일반적인 JOIN의 종류이며 교집합

동등 JOIN(Equi-JOIN)이라고도 하며, N개의 테이블 JOIN 시 **N-1개의 JOIN 조건**이 필요

```sql
-- ON을 이용한 JOIN 조건 지정
table1 INNER JOIN table2
ON table1.column = table2.column;

-- USING을 이용한 JOIN 조건 지정
table1 INNER JOIN table2
USING 공통column;

-- NATURAL JOIN
SELECT col1, col2, ..., colN
FROM table1 NATURAL JOIN table2;
```

<br>

### OUTER JOIN

<br>

LEFT OUTER JOIN, RIGHT OUTER JOIN, FULL OUTER JOIN으로 구분

어느 한 쪽 테이블에는 해당하는 데이터가 존재하는데 다른 쪽 테이블에는 데이터가 존재하지 않을 경우 그 데이터가 검색되지 않는 문제점을 해결하기 위해 사용

<br>

#### LEFT OUTER JOIN

<br>

왼쪽 테이블을 기준으로 JOIN 조건에 일치 하지 않는 데이터까지 출력

```sql
SELECT col1, col2, ..., colN
FROM table1 LEFT OUTER JOIN table2
ON or USING;
```

<br>

#### RIGHT OUTER JOIN

<br>

오른쪽 테이블을 기준으로 JOIN 조건에 일치 하지 않는 데이터까지 출력

```sql
SELECT col1, col2, ..., colN
FROM table1 RIGHT OUTER JOIN table2
ON or USING;
```

<br>

#### FULL OUTER JOIN

<br>

양쪽 테이블을 기준으로 JOIN 조건에 일치 하지 않는 데이터까지 출력

MySQL은 지원하지 않는다.

```sql
SELECT col1, col2, ..., colN
FROM table1 FULL OUTER JOIN table2
ON or USING;
```

<br>

### SELF JOIN

<br>

같은 테이블끼리 JOIN

<br>

### None-Equi JOIN

<br>

table의 PK, FK가 아닌 일반 column을 JOIN 조건으로 지정