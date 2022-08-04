## 큐

스탯과 마찬가지로 삽입과 삭제의 위치가 제한적인 자료구조

큐의 뒤에서는 삽입만 하고, 큐의 앞에서는 삭제만 이루어지는 구조

큐

머리(front) 마지막으로 삭제된 원소

꼬리(rear) 마지막으로 들어온 원소

원소 삽입 enQueue

원소삭제 deQueue



java.util.Queue

큐에 필요한 연산을 선언해 놓은 인터페이스

LinkedList 클래스를 Queue 인터페이스의 구현체호 많이 사용

offer()

poll()

isEmpty()

size()