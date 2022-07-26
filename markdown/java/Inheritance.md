```java
Book[] containTitle = bm.searchByTitle("Java");
	for (Book t : containTitle) {
    	// Magazine 타입이 들어와도 캐스팅 필요 없다.
		// 메서드가 오버라이드(재정의) 되었다면 무조건 자식 클래스에서 재정의된 메서드가 호출된다.
		System.out.println(t);
	}
```