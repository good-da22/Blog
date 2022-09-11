## RDBMS

<br>

관계형(Relational) 데이터베이스 시스템

테이블 기반(Table based)의 DBMS

데이터를 테이블 단위로 관리 - 하나의 테이블은 여러 개의 컬럼(Column)으로 구성

중복 데이터를 최소화 - 같은 데이터가 여러 컬럼 또는 테이블에 존재 했을 경우, 데이터를 수정 시 문제 발생 가능성이 높아짐, 정규화

여러 테이블에 분산되어 있는 데이터를 검색 시 테이블 간의 관계(join)를 이용하여 필요한 데이터를 검색

<br>

## SQL (Structured Query Language)

<br>

Database에 있는 정보를 사용할 수 있도록 지원하는 언어

모든 DBMS에서 사용 가능

대소문자는 구별하지 않는다.(데이터의 대소문자는 구분)

<br>

### DDL (Data Definition Language)

<br>

DDL (Data Definition Language) : 데이터 정의어

데이터베이스 객체(table, view, index, ...)의 구조를 정의 (생성, 변경, 제거)

테이블 생성, 컬럼 추가, 타입 변경, 제약조건 지정, 수정 등

- CREATE : 데이터베이스 객체를 생성
- DROP : 데이터베이스 객체를 삭제
- ALTER : 기존에 존재하는 데이터베이스 객체를 수정

<br>

### DML (Data Manipulation Language)

DML (Data Manipulation Language) : 데이터 조작어

data 조작 가능

테이블의 레코드를 CRUD (Create, Retrieve, Update, Delete)

개별적으로 Database 테이블에서 새로운 행을 입력하고, 기존의 행을 변경, 제거

- INSERT : 데이터베이스 객체에 데이터를 입력, Create
- SELECT : 데이터베이스 객체에서 데이터를 조회, Retrieve
- UPDATE : 데이터베이스 객테에 데이터를 수정, Update
- DELETE : 데이터베이스 객체에 데이터를 삭제, Delete

<br>

### DCL (Data Control Language)

<br>

DCL (Data Control Language) : 데이터 제어어

DB, Table의 접근권한이나 CRUD 권한을 정의

특정 사용자에게 테이블의 검색권한 부여 / 금지 등

- GRANT : 데이터베이스 객체에 권한을 부여
- REVOKE : 데이터베이스 객체 권한 취소

<br>

### TCL (Transaction Control Language)

TCL (Transaction Control Language) : 트랜잭션 제어어

transaction : 데이터의 논리적 연산 단위

- COMMIT : 실행한 Query를 최종적으로 적용
- ROLLBACK : 실행한 Query를 마지막 COMMIT 전으로 취소시켜 데이터를 복구

<br>

### 데이터베이스 생성, 변경, 제거

<br>

#### 데이터베이스 생성

<br>

```sql
create database 데이터베이스 명
```

```sql
create database 데이터베이스 명
default character set 값
collate 값;
```

character set : 각 문자가 컴퓨터에 저장될 때 어떠한 '코드'로 저장될지에 대한 규칙의 집합

collation : 특정 문자 셋에 의해 데이터베이스에 저장된 값들으 비교, 검색하거나 정렬 등의 작업을 위해 문자들을 서로 '비교'할 때 사용하는 규칙들의 집합

<br>

#### 데이터베이스 변경

<br>

```sql
alter database 데이터베이스 명
default character set 값
collate 값;
```

<br>

#### 데이터베이스 삭제 및 사용

```sql
# 데이터베이스 삭제
drop database 데이터베이스 명;
```

```sql
# 데이터베이스 사용
use 데이터베이스 명
```

<br>

### table 생성

<br>

**스키마** : 데이터베이스의 테이블에 저장될 데이터의 구조와 형식을 정의

**ER Diagram(ERD)** : 개체 타입과 관계 타입을 기본 개념으로 현실 세계를 개념적으로 표현하는 방법

<br>

#### data type

<br>

**문자형 데이터 타입**
- CHAR[(M)] : 고정 길이를 갖는 문자열을 저장, M은 1 ~ 255 (2^8 - 1), 정해진 길이보다 짧은 문자를 저장하더라도 정해진 길이 만큼 기억장소를 차지

- VARCHAR[(M)] : 가변 길이를 갖는 문자열을 지정, M은 1 ~ 65535 (2^16 - 1), 실제 입력된 문자열 길이 만큼 기억장소를 차지

- TINYTEXT[(M)] : 최대 255 (2^8 - 1) byte
  
- TEXT[(M)] : 최대 65535 (2^16 - 1) byte
  
- MEDIUMTEXT[(M)] : 최대 16777215 (2^24 - 1) byte
  
- LONGTEXT[(M)] : 최대 4294967295 (2^32 - 1) byte
  
- ENUM('value1', 'value2', ...) : 열거형, 정해진 몇가지의 값들 중 하나만 저장, 최대 65535개의 개별 값을 가질 수 있고, 내부적으로 정수 값으로 표현
  
- SET('value1', 'value2', ...) : 집합형, 정해진 몇가지의 값들 중 여러 개를 저장, 최대 64개의 요소로 구성될 수 있고, 내부적으로는 정수 값

<br>

**숫자형 데이터 타입**
- BIT[(M)] : 1byte, 비트 값 유형, M은 값당 비트 수를 나타내며 1에서 64 사이의 값을 나타냄

- BOOL, BOOLEAN : TINYINY(1)의 동의어, 0은 false, 0아닌 값은 true로 간주

- TINYINT[(M)] : 1byte, (signed) -128 ~ 127, (unsigned) 0 ~ 255(2^8)

- SMALLINT[(M)] : 2byte, (signed) -32768 ~ 32767, (unsigned) 0 ~ 65535(2^16)

- MEDIUMINT[(M)] : 3byte, (signed) -8388608 ~ 8388607, (unsigned) 0 ~ 16777215(2^24)

- INT[(M)] : 4byte, (signed) -2147483648 ~ 2147483647, (unsigned) 0 ~ 4294967295(2^32)

- BIGINT[(M)] : 8byte, (signed) -9223372036854775808 ~ 9223372036854775807, (unsigned) 0 ~ 18446744073709551615(2^64)

- FLOAT[(M, D)] : 4byte, (signed) -3.402823466E+38 ~ 1.175494351E-38, (unsigned) 1.175494351E-38 ~ 3.402823466E+38

- DOUBLE[(M, D)]
- DOUBLE PRECISION[(M, D)]
- REAL[(M, D)]
    
    8byte, (signed) -1.7976931348623157E+908 ~ -2.2250738585072014E-308, (unsigned) 2.2250738585072014E-308 ~ 1.7976931348623157E+308

- FLOAT(p) : 부동 소수점 숫자, p는 비트의 정밀도를 가리키지만 MySQL은 결과 데이터 타입으로 FLOAT 또는 DOUBLE을 사용할지를 결정할 때에만 이 값을 사용한다.

- DECIMAL[(M[, D])]

    묶음 고정 소수점 숫자

    M은 전체 자릿수(Precision : 정밀도), D는 소수점 뒷 자리수(Scale : 배율)

    최대 65자리까지 지원

- DEC[(M[, D])]
- NUMERIC[(M[, D])]
- FIXED[(M[, D])]

    DECIMAL과 동의어

    FIXED 동의어는 다른 데이터베이스 시스템과의 호환을 위해서 사용

<br>

**날짜형 데이터 타입**
- DATE : 3byte, YYYY-MM-DD('1001-01-01' ~ '0000-12-31')

- TIME : 3byte, HH:MM:SS('-838:59:59' ~ '838:59:59')
  
- DATETIME : 8byte, YYYY-MM-DD HH:MM:SS('1001-01-01 00:00:00' ~ '9999-12-31 23:59:59')

- TIMESTAMP[(M)] : 4byte, 1970-01-01 ~ 2038-01-19 04:14:07 까지 지원(1970-01-01 00:00:00를 0으로 해서 1초단위로 표기), index가 더 빠르게 생성

- YEAR[(2|4)] : 1byte, 2와 4를 지정할 수 있으며, 2인 경우 값의 범위는 70 ~ 69, 4인 경우에는 1970 ~ 2069

<br>

**이진 데이터 타입**
- BINARY[(M)] : CHAR 유형과 유사하지만 이진 바이트 문자열을 이진이 아닌 문자열로 저장, M은 바이트 단위의 열 길이를 나타냄

- VARBINARY[(M)] : VARCHAR 유형과 유사하지만 이진 바이트 문자열을 이진이 아닌 문자열로 저장, M은 바이트 단위의 열 길이를 나타냄

- TINYBLOB[(M)] : 이진 데이터 타입, 최대 255 (2^8 - 1) byte

- BLOB[(M)] : 이진 데이터 타입, 최대 65535 (2^16 - 1) byte

- MEDIUMBLOB[(M)] : 이진 데이터 타입, 최대 16777215 (2^24 - 1) byte

- LONGBLOB[(M)] : 이진 데이터 타입, 최대 4294967295 (2^32 - 1) byte

<br>

#### Optional attributes

```sql
create table 테이블 이름 (
    column_name1 Type [optional attributes],
    column_name2 Type,
    ...
    column_nameN Type
);
```

- NOT NULL : 각 행은 해당 열의 값을 포함해야 하며 null 값은 허용되지 않음

- DEFAULT value : 값이 전달되지 않을 때 추가되는 기본값 설정

- UNSIGNED : Type이 숫자인 경우만 해당되며 숫자가 0 또는 양수로 제한됨

- AUTO INCREMENT : 새 레코드가 추가 될 때마다 필드 값을 자동으로 1 증가시킴

- PRIMARY KEY : 테이블에서 행을 고유하게 식별하기 위해 사용, PRIMARY KEY 설정이 있는 열은 일반적으로 ID 번호이며 AUTO INCREMENT와 같이 사용되는 경우가 많음

<br>

#### 제약조건

<br>

컬럼에 저장될 데이터의 조건을 설정

제약조건을 설정하면 조건에 위배되는 데이터는 저장 불가

테이블 생성시 컬럼에 직접 지정하거나 constraint로 지정, 또는 ALTER를 이용하여 설정가능

- NOT NULL : 컬럼에 NULL 값을 저장할 수 없고, 반드시 쿼리문을 이용하여 값을 지정

- UNIQUE : 컬럼에 중복된 값을 저장 할 수 없음, NULL 값은 허용

- PRIMARY KEY : 컬럼에 중복된 값을 저장 할  수 없고, NULL 값도 허용하지 않는다. 주로 ROW를 구분하기 위한 유일한 값을 지정할 때 사용, '기본키'라고 부른다.

- FOREIGN KEY : 특정 테이블의 PK 컬럼에 저장되어 있는 값만 저장, '참조키', '외래키' 라고 부름, NULL 값은 허용, references를 이용하여 어떤 컬럼에 어떤 데이터를 참조하는지 반드시 지정

- DEFAULT : NULL 값이 들어올 경우 기본 설정되는 값을 지정

- CHECK : 값의 범위나 종류를 지정, MYSQL 8.0.16부터 사용가능(이전 버전의 경우 설정은 되나 적용이 안된다.)