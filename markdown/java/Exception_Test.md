## Exception

## #41
체크 예외 - 트라이 캐치 필요

언체크 예외 - 개발자가 책임을 져라 컴파일은 진행한다.

예외를 발생시키는 경우 던지거나 `throws - throw` 

직접 해결하거나 `try - catch`

```java
        int[] intArray = {10};
        
        System.out.println(intArray[2]); // 인덱스 범위 초과
        // java.lang.ArrayIndexOutOfBoundsException
        // 컴파일 시점에서는 오류로 잡고 있지 않는다.
        // unchecked Exception 계열
```

## #43

```java
		try {
			System.out.println(intArray[2]); // 예외 발생
		} catch (ArrayIndexOutOfBoundsException e) { // JVM에 ArrayIndexOutOfBoundsException 객체 생성
			System.out.println(e.getMessage()); //ArrayIndexOutOfBoundsException.getMessage() -> 에외가 발생한 인덱스 번호를 넘겨준다.
		}

		System.out.println("프로그램 종료합니다.");
```

## #44

printStackTrace() -> 메소드 호출 스택 -> 디버깅 수단으로만 활용할 것

사용시 외부에 프로그램 정보( 메서드 호출 스택 )가 노출된다.

```java
if(isDebug == true) {
        e.printStackTrace();
}
```

## #45

잘못된 예외를 던져 캐치블록을 만나지 못하는 경우 비정상 종료된다.

## #46
```java
public class ExceptionHandlingFlow {
    public static void main(String[] args) {
        int num = new Random().nextInt(2);
        try {
            System.out.println("code 1, num: " + num);
            int i = 1 / num; // num : 0일 때 new XXXException 생성, catch 블록으로
            System.out.println("code 2 - 예외 없음: "+ i);
            return; // main에서 return시 프로그램 종료
        } catch (ArithmeticException e) {
            System.out.println("code 3 - exception handling 완료");
        } finally {
            System.out.println("code 4 - 언제나 실행"); // finally 코드블록 먼저 실행 후 return 된다.
        }
        System.out.println("code 5");
    }
    
//    code 1, num: 0
//    code 3 - exception handling 완료
//    code 4 - 언제나 실행
//    code 5
    
//    code 1, num: 1
//    code 2 - 예외 없음: 1
//    code 4 - 언제나 실행

}

```

## #57
메인 메서드에서 throws 사용 시 JVM에게 예외를 던진다.

uncheckedException (RuntimeException) 따로 throws 없어도 전달이 된다. 전달되고 나서 결국은 try - catch로 해결해야 한다.

코드 작성은 간편해지나 눈으로 예외를 즉각적으로 파악하기 어렵다. 실행을 해야 알 수 있다.

checkedException 은 throws 하거나 try-catch로 해결

## #61
API 에서 예외 발생시 던지는 이유

개발자가 예외가 발생했음을 인지하고 적절하게 처리를 유도하기 위해

## #67
문제 발생 가능성을 조건문을 통해 처리하는 것이 좋다

디버깅의 대상으로 예외의 처리 대상으로 생각하지 말것

