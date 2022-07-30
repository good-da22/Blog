## Collection

## #76
장점 " 배열, 인덱스 번호로 바로 접근 => 빠르다

단점, 크기 변경 불가. 새로운 배열 생성 후 복사해 사용

## #77
연결 리스트

순차 추가/수정/삭제 느림

비 순차 추가/수정/삭제 빠름

조회 매우 느림

## #79
삭제하면 사이즈가 줄어든다. 앞으로 땡겨진다.

반대로 접근해서 탐색하는 것이 편하다.

크기가 가변적이다.

## #80
for - each 사용 시 collection 크기는 불변해야한다.

그냥 사용하면 잘못된 인덱스에 접근하게 된다. 예외 발생

리스트 내의 데이터가 변함이 없을 때만 향상된 for 문 사용, 읽기 전용

## set

## #82
대부분 hash set 사용

순서가 있겠금 사용하고싶다면 Tree set 사용

## #84
set 동일한 객체 탐지

equals()가 트루이고 hashCode()가 같을 것

하나라도 다르면 같은 객체 X

set은 인덱스가 없기 때문에 삭제를 하고자하는 동일한 객체를 파라미터로 넘겨줘야 한다. remove()

## Map

## #86
맵 - 엔트리를 감싸고 있다

엔트리 - 키와 값으로 이루어져 있다., 맵에서의 한 행

주로 사용 - 해쉬 맵

정렬 관련 - 트리 맵

## #87
put(키, 벨류) - 키와 벨류는 제네릭타입, 어떤 타입이든 사용 가능

컨테인키, 컨테인벨류 - 불리언(포함여부) 반환

엔트리셋, 엔트리(맵의 한 행)을 셋에 담아서 반환

키셋, 키 값들 만 셋에 담아서 반환

겟 - 해당 키의 벨류를 가져온다

사이즈 - 행(엔트리)의 개수

수정 - 해당하는 키값에 벨류를 새로 주기

```java
// 값을 통해서 해당하는 키 값 찾기  
    	Set<Map.Entry<String, String>> entrySet = hMap.entrySet();
    	for(Map.Entry<String, String> entry : entrySet) {
    		if(entry.getValue().equals("4567")) {    			
    			System.out.println(entry.getKey());
    		}
    	}
```

## 정렬

## #89

정렬은 순서를 가지고 있어야 한다

리스트, SortedSet(트리셋), SortedMap(트리맵) -> sort 인터페이스를 상속받은 자식들

## #90
정렬을 위해 구현, 정렬하고자 하는 타입을 제네릭 타입 파리미터로

## #91
```java
// String 객체끼리 글자 길이 비교, 으름차순 정렬
public class StringLengthComparator implements Comparator<String>{

	@Override
	public int compare(String o1, String o2) {
		int len1 = o1.length();
		int len2 = o2.length();	
		return Integer.compare(len1, len2);
//		return Integer.compare(len2, len1); // 역순으로 정렬 가능!
	}
}
/****************************************************/
Collections.sort(names, new StringLengthComparator());
```

## #93

new 연산자 다음 바로 인터페이스 compartor

클래스 이름과 implements 키워드 생략, 이름없는 클래스로 객체 생성

익명 클래스 - 1회성 기능 사용을 위해, 사용하기위해선 클래스를 객체화 할 필요가 있다.

자바 - 객체지향 프로그래밍 -> 클래스가 필요 -> 클래스를 객체화 -> 실행

- - -

람다식 - 자바8부터 지원, 함수형 프로그래밍 형태 지원

람다식 & 스트림 => 선택사항, 코드 간결화 가능, 함수형 프로그래밍 지원

람다식 - 구현부가 한 줄인 경우 중괄호 {} 생략 가능 & 그 한줄이 리턴되는 값으로 판단, return 키워드 생략 가능

```java
	Collections.sort(names, (o1, o2) -> // 메서드의 파라미터 부분, 화살표 기준 오른편은 구현 부분
                                        // 타입은 인터페이스를 보고 유추, 생략 가능
		Integer.compare(o1.length(), o2.length()) // 메서드 구현 부, 한줄로 작성하면 return 생략 가능
	);

```

offline5 참고

```java
MyFunction2 test = () -> System.out.println("test"); // 함수에 다른 함수를 파라미터로 전달
		function(test); // 다른 함수에 전달되는 함수 == 일급객체, 일급 객체를 쓸 수 있다 => 함수형 프로그래밍 언어
```

```java
// 함수형 인터페이스 (람다식을 다루기 위한 인터페이스)
// 제약조건: 오직 하나의 추상 메서드만 정의되어 있어야 한다.
// static 메서드와 default 메서드의 개수에는 제약이 없다.
@FunctionalInterface // 함수형 인터페이스인지 검사
public interface FunctionalInterface {
	public abstract int method(test); // 다른 함수에 전달되는 함수 == 일급객체, 일급 객체를 쓸 수 있다 => 함수형 프로그래밍 언어

// 2-2.
method(() -> System.out.println("test"));

// 3-1. 변수명 = 람다식 매개변수 -> { 구현/리턴 내용 };
FunctionalInterface sum0 = (int x1, int x2) -> { return x1 + x2; };

// 3-2. 구현 내용이 한 줄일 경우 return 키워드 생략 가능
FunctionalInterface sum1 = (int x1, int x2) -> x1 + x2;

// 3-3. 구현 내용이 여러 줄일 경우
FunctionalInterface sum2 = (int x1, int x2) -> {
	System.out.println(x1 + x2);
	return x1 + x2;
};

// 3-4. 데이터 추론 가능 매개변수 데이터타입 생략 가능, 인터페이스 선언부를 보고 파라미터 타입을 판단
FunctionalInterface sum3 = (x1, x2) -> x1 + x2;
```(int a, int b);
}
```

매개변수의 개수, 반환 여부에 따라 함수형 인터페이스 사용 가능
```java
import java.util.function.BiConsumer;
import java.util.function.BiFunction;
import java.util.function.BiPredicate;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Predicate;
import java.util.function.Supplier;

/**
 * java.util.function 패키지 활용
 *  offline5.basic3 참고
 */
 ```

 
