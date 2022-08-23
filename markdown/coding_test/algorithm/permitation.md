## 순열(Permutation)

<br><br>

서로 다른 것들 중 몇 개를 뽑아서 한 줄로 나열하는 것

서로 다른 n개중 r개를 선택하는 순열

---

$_nP_r$

$_nP_r = n * (n-1) * (n-2) * ... * (n-r+1)$

$_nP_n = n! = n * (n-1) * (n-2) * ... 2 * 1$

---

<br>

다수의 알고리즘 문제들은 순서화된 요소들의 집합에서 최선의 방법을 찾는 것과 관련 있다.

N 개의 요소들에 대해서 n!개의 순열이 존재

12! = 479,001,600

n > 12 인 경우, 시간 복잡도 폭발적으로 증가

<br>

순열과 조합의 차이 - 순서가 의미가 있는가?

**순서가 의미가 있으면** : 순열

**순서가 의미가 없으면** : 조합

<br>

### 재귀 호출을 통한 순열 생성

<br>

```
numers[]        // 순열 저장 배열
isSelected[]    // 인덱스에 해당하는 숫자가 사용 중인지 저장하는 배열

perm(cnt)       // cnt : 현재까지 뽑은 순열 수의 개수
    IF cnt == R
    순열 생성 완료
    ELSE
        for i from 0 to N-1
            if isSelected[i] == true then continue
            numbers[cnt] <- i
            isSelected[i] <- i
            perm(cnt + 1)
            isSelected[i] <-  false
        end for

```

<br><br>

## 조합

<br>

서로 다른 n개의 원소 중 r개를 순서 없이 골라낸 것을 조합(Combination)이라고 부른다

$_nC_r = {n! \over (n-r)!r!}$

$_nC_r = _{n-1}C_{r-1} + -_{n-1}C_r$ -> 재귀적 표현

$_nC_0 = 1$

$_nC_{n/2}$ -> 경우의 수가 제일 크다

<br>

### 재귀 호출을 통한 조합 생성

```
nCr -> n개 원소 중 r개 원소를 갖는 조합 생성
input[] // n개의 원소를 가지고 있는 배열
numbers[] // r개의 크기의 배열, 조합이 저장될 배열

comb(cnt, start) // cnt : 현재까지 뽑은 조합 원소 개수, start : 조합 시도할 원소의 시작 인덱스
    if cnt == r
        조합 생성 완료
    else
        for i from start to n-1
            numbers[cnt] <- input[i]
            comb(cnt + 1, i + 1)
        end for
end comb()    
```

<br><br>

## Next Permutation

현 순열에서 사전 순으로 다음 순열 생성

현재 순열 상태에서 다음으로 큰 순열

#### 알고리즘

배열을 오름차순으로 정렬한 후 시작, 가장 작은 순열에서 시작

아래의 과정을 반복하여 사전순으로 다음으로 큰 순열 생성(가장 큰 내림차순 순열을 만들 때까지 반복)

nPn 만 가능

1. 뒤쪽부터 탐색(가중치가 낮은 자리부터)하여 교환위치(i-1) 찾기(i : 꼭대기)
2. 뒤쪽부터 탐핵하여 교환위치(i-1)와 교환할 큰 값 위치(j)찾기
3. 두 위치 값(i-1, j 교환)
4. 꼭대기위치(i)부터 맨 뒤까지 오름차순 정렬