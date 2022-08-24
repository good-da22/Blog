## 분할 정복(Divide and Conquer)

<br>

**분할(Divide)** : 해결할 문제를 여러 개의 작은 부분으로 나눈다.

**정복(Conquer)** : 나눈 작은 문제를 각각 해결한다.

**통합(Combine)** : (필요하다면) 해결된 해답을 모은다.

<br>

### 거듭 제곱

<br>

#### 반복(Iterative) 알고리즘

<br>

시간 복잡도 : $O(n)$

```
Iterative_Power(x, n)
    result <- 1

    FOR i in 1 -> n
        result <- result * x
    
    RETURN result
```

<br>

#### 분할 정복 기반 알고리즘

<br>

시간 복잡도 : $O(log_2n)$

```
Recursive_Power(x, n)
    IF n == 1 : RETURN x
    IF n is even
        y <- Recursive_Power(x, n/2)
        RETURN y * y
    ELSE
        y <- Recursive_Power(x, (n-1)/2)
        RETURN y * y * x
```

<br><br>

### 이진 탐색

<br>

자료 가운데의 항목의 키 값과 비교하여 다음 검색의 위치를 결정하고 검색을 계속 진행하는 방법

목적 키를 찾을 때까지 이진 검색을 순환적으로 반복 수행, 검색 범위를 반으로 줄여가며 보다 빠르게 검색을 수행

이진 검색을 하기 위해서는 자료가 정렬된 상태여야 한다.

<br>

#### 검색 과정

<br>

1. 자료의 중앙에 있는 원소를 고른다.
2. 중앙 원소의 값과 찾고자 하는 목표 값을 비교한다
3. 중앙 원소의 값과 찾고자 하는 목표 값이 일치하면 탐색을 끝낸다
4. 목표 값이 중앙 원소의 값보다 작으면 왼쪽, 크면 오른쪽에 대해 탐색을 실행
5. 찾고자 하는 값을 찾을 때 까지 위 과정을 반복

<br>

### java.util.Arrays.binarySearch

<br>

정렬된 배열을 전달해야 한다.

int binarySearch(int[] a, int key)

int binarySearch(int[] a, int fromIdex, int toIndex, int key)

찾은 원소의 인덱스 반환

못 찾을 경우, 음수 값 -> 만약 존재한다면 있어야하는 자리의 인덱스(-삽입index - 1)