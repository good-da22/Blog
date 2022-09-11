## Data Manipulation Language (DML)

<br>

INSERT : 데이터베이스 객체에 데이터를 입력, create

SELECT : 데이터베이스 객체에서 데이터를 조회, retrieve

UPDATE : 데이터베이스 객체에 데이터를 수정, update

DELETE : 데이터베이스 객체에 데이터베이스를 삭제, delete

<br>

### INSERT

<br>

```sql
INSERT INTO table_name
VALUES(col_val1, col_val2, ... , col_valN);

INSERT INTO table_name (col_name1, col_name2, ... , col_nameN)
VALUES(col_val1, col_val2, ... , col_valN);

INSERT INTO table_name (col_name1, col_name2, ... , col_nameN)
VALUES(col_val1, col_val2, ... , col_valN),
      (col_val1, col_val2, ... , col_valN);
```

생략이 가능한 field

1. NULL이 허용된 컬럼
2. DEFAULT가 설정된 컬럼
3. AUTO INCREMENT가 설정된 컬럼

<br>

### UPDATE

<br>

```sql
UPDATE table_name
SET col_name1 = col_val1, [col_name2 = col_val2, ... , col_nameN = col_valN]
WHERE conditions;
```

WHERE절의 conditions(조건)에 만족하는 레코드의 값을 변경

WHERE절을 생략하면 **모든 데이터**가 바뀐다.

<br>

### DELETE

<br>

```sql
DELETE from table_name
WHERE conditions;
```

WHERE절의 conditions(조건)에 만족하는 레코드의 값을 삭제

WHERE절을 생략하면 **모든 데이터**가 삭제된다.

<br>

### SELECT

<br>

#### SELECT clause

<br>

```sql
SELECT * | { [ALL | DISTINCT] column | expression | [alias], ... }
FROM table_name;
```

SELECT clause 와 FROM clause은 필수

- &#42; : FROM 절에 나열된 테이블에서 모든 열을 선택

- ALL : 선택된 모든 행을 반환
  
- DISTINCT : 선택된 모든 행 중에서 중복 행 제거
  
- column : FROM 절에 나열된 테이블에서 지정된 열을 선택
  
- expression : 표현식은 값으로 인식되는 하나 이상의 값, 연산자 및 SQL 함수의 조합을 뜻함

- alias : 별칭

- CASE WHEN exp THEN exp [, WHEN exp THEN exp] ELSE exp : 조건에 따른 적용

<br>

#### WHERE clause

<br>

```sql
SELECT * | { [ALL | DISTINCT] column | expression | [alias], ... }
FROM table_name
WHERE conditions;
```

WHERE clause : 조건에 만족하는 행을 검색

- condition AND condition
  
- condition OR condition
  
- NOT condition
  
- IN (condition1, condition2, ... , conditionN)
  
- condition BETWEEN condition and condition
  
- condition IS NULL

- condition IS NOT NULL

- condition LIKE (wild card : %, _)

<br>

#### ORDER BY clause

<br>

```sql
SELECT * | { [ALL | DISTINCT] column | expression | [alias], ... }
FROM table_name
WHERE conditions
ORDER BY col_name1 [ ASC | DESC ] [, col_name2, ...];
```

ORDER BY clasue : 정렬(default : ASC)

- ORDER BY col_name1 (ASC) : 오름차순, default

- ORDER BY col_name1 DESC : 내림차순

- ORDER BY col_name1, col_name2, ... : col_name1 정렬 후 col_name2 정렬