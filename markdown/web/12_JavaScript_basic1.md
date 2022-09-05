## JavaScript 기본문법

<br>

### 주석(comment)

<br>

주석은 JavaScript 코드에 대한 부연 설명이므로 실행 코드에 포함되지 않는다.

JavaScript 주석은 한 줄 주석(Line Comment)과 블록 주석(Block Comment)이 있다.

한 줄 주석은 //code로 표기하고, 블록 주석은 /* code */ 로 표기한다.

가능하면 블록 주석보다 라인 주석을 사용한다.


<br>

### 변수(varidable)

<br>

JavaScript는 변수를 선언할 때 타입을 명시하지 않고 **var** keyword를 사용하여 선언

JavaScript는 동적타입(Dynamic / Weak type) 언어. **변수의 타입 지정없이** 값이 할당되는 과정에서 자동으로 변수의 타입이 결정

같은 변수에 여러 타입의 값을 할당 가능

변수의 이름은 함수 이름과 혼동되지 않도록 유일한 이름을 사용(변수[형용사, 명사] , 함수[동사] 사용)

JavaScript는 ECMAScript 표준에 따라 낙타 표기법(Camel case)를 사용

낙타 표기법이란 기본적으로 소문자로 작성하되 2개 이상의 단어일 경우 단어의 첫 글자는 대분자로 표기

키워드, 공백 문자 포함, 숫자로 시작 X

특수 문자는 _ 와 $ 허용

<br>

### 자료형(data type)

<br>

프로그램은 정적인 데이터 값을 동적으로 변환해 가면서 원하는 정보를 얻는다.

프로그램에서 다루는 데이터 값의 종류들을 자료 형(data type)이라 표현

JavaScript에서는 자료 형을 원시 타입(primitive type)과 객체 타입(object type)으로 분류

원시 타입에는 숫자, 문자열, boolean, null, undefined와 같이 5가지가 존재, 이를 제외한 모든 값은 객체 타입

- 숫자형 : number, 정수 또는 실수형
- 문자열형 : string, 문자, single or double quotation으로 표기
- boolean형 : boolean, 참(true) or 거짓(false)
- undefined : undefined, 변수가 선언되었지만 초기화가 되지 않을 경우
- null : object, 값이 존재하지 않을 경우

<br>

#### 숫자형(number)

<br>

JavaScript는 숫자를 정수와 실수로 나누어 구분하지 않는다.

모든 숫자를 8byte의 실수 형태로 처리(정수만을 표현하기 위한 데이터 타입은 없다, 실수로 처리)

편의성을 위해 정수 리터럴과 실수 리터럴을 제공

숫자의 연산 처리시 실수 형태로 하기 때문에 특정 소수점을 정확하게 표현하지 못함

기본 연산 기호는 Java나 C++과 같은 일반 프로그래밍 언어와 같다.

**부동소수점 오류**

```javascript
var x = 0.3 - 0.3;
var y = 0.2 - 0.1;
console.log(x == y)     // false
console.log(x);         // 0.09999999999999998
console.log(y);         // 0.1
```

**정확한 계산이 필요한 경우**

```javascript
var a = 0.3;
var b = 0.2;

var result = (a * 10 - b * 10) / 10;
console.log(result);                    // 0.1 
```

<br>

JavaScript는 언더플로우, 오버플로우, 0으로 나누는 연산에 대해 예외를 발생 시키지 않는다.

JavaScript에는 숫자와 관련된 특별한 상수가 존재한다.

Infinity : 무한대를 나타내는 상수, 어떠한 수를 0으로 나누거나 Infinity를 어떠한 수로 사칙연산한 결과

NaN(Not a Number) : 계산식의 결과가 숫자가 아님을 나타내는 상수

<br>

#### 문자열

<br>

JavaScript에서 문자열은 16비트의 Unicode 문자를 사용

문자 하나를 표현하는 char와 같은 문자형은 제공하지 않는다. 'a'와 같은 한글자도 문자열로 표현

작은 따옴표(' , single quotes) 도는 큰 따옴표(" , double quotes) 둘 다 사용 가능, 혼용 불가

이스케이프 시퀀스(`\`)도 사용 가능

백틱(`)을 이용한 문자열 표현(ES6 템플릿 리터럴) 사용 가능

<br>

#### boolean, null 과 undefined

<br>

boolean은 비교 연산의 결과값으로 true 또는 false 중 하나의 값을 갖는다.

**비어 있는 문자열, null, undefined, 숫자 0은 false로 간주**

**null**은 값이 없거나 비어 있음을 의미

**undefined**는 값이 초기화되지 않았음(정의되지 않음)을 의미

null과 undefined는 의미가 비슷하지만 값을 할당 하지 않은 변수는 undefined가 할당(시스템 레벨)

코드에서 명시적으로 값이 없음을 나타낼 때(프로그램 레벨)는 null을 사용

<br>

#### 자동 형변환(동적 타이핑, Dynamic Typing)

<br>

JavaScript는 Java나 C++등과 같은 언어와는 달리 자료형에 대해 매우 느슨한 규칙이 적용

어떤 자료 형이든 전달할 수 있고, 그 값을 필요에 따라 변환 가능

서로 다른 자료 형의 연산이 가능

모든 자료 형을 var로 선언하기 때문에 변수 선언은 쉽지만 이런 느슨한 규칙 때문에 혼란을 야기

<br>

### 변수 호이스팅(Variable Hoisting)

<br>

var 키워드를 사용한 변수는 중복해서 선언이 가능

호이스팅이란, var 선언문이나 function 선언문 등 모든 선언문이 해당 Scope의 처음으로 옮겨진 것처럼 동작하는 특성

JavaScript는 모든 선언문이 선언되기 이전에 참조가 가능

변수의 생성
 - 선언 단계 : 변수 객체에 변수를 등록
 - 초기화 단계 : 변수 객체에 등록된 변수를 메모리에 할당. undefined로 초기화
    
    해당 두 단계는 한 번에 이루어 진다.

 - 할당 단계 : undefined로 초기화된 변수에 실제 값을 할당

Hoisting 되어 undefined로 초기화(선언, 초기화단계가 실행)

실제 할당은 값이 주어지는 코드에서 일어난다.

JavaScript는 블록 레벨 스코프를 가지지 않고 함수 레벨 스코프만 갖는다.

ES6 이후에서 const, let 사용

<br>

### 상수(constant)

<br>

ECMAScript6 이전까지는 상수 표현을 지원하지 않음

변수의 값을 변경하면 안 되는 상수와 일반 변수를 구분하고자 변수 명명 규칙을 다르게 하여 사용

상수의 표기법은 모든 문자를 대문자로 사용하고 단어 사이는 '_'로 표기

ECMAScript6에서는 `const` keyword가 추가되어 **상수**를 지원

<br>

#### let & const

<br>

ECMAScript5까지는 식별자에 값을 넣는 변수의 기능은 var 키워드만 사용

ECMAScript6부터는 let과 const 키워드 추가

- var : 변수, 전역 스코프, 재선언 가능
- let : 변수, 해당 스코프, 재선언 불가능
- const : 상수, 해당 스코프, 재선언 불가능

<br>

### 연산자(operator)

<br>

- `delete` : 프로퍼치를 제거
- `typeof` : 피연산자 타입을 리턴
- `void` : undefined 값을 알려줌
- `>>>` :  부호비트 확장 없이 값을 오른쪽으로 이동
- `instanceof` : 객체가 특정 객체의 타입인지를 확인
- `in` : 프로퍼티가 존재하는지 확인 
- `===` : 값이 일치하는지 확인(타입 포함)
- `!===` : 값이 일치하지 않는지 확인(타입 포함)
- `?:` : 조건에 해당하는 구문을 수행
- `,` : 1번째 구문은 버리고 다음 구문 값을 반환

<br>

### 조건문, 반복문

<br>

기본 Java, C++ 문법과 유사

<br>

#### 조건문

<br>

if - else if - else

switch

<br>

#### 반복문

<br>

while

do / while

for