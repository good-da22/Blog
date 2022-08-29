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

## 조합(combination)

<br>

서로 다른 n개의 원소 중 r개를 순서 없이 골라낸 것을 조합(Combination)이라고 부른다

---

$_nC_r = {n! \over (n-r)!r!}, (n >= r)$

$_nC_r = _{n-1}C_{r-1} + -_{n-1}C_r$ -> 재귀적 표현

$_nC_0 = 1$

$_nC_{n/2}$ -> 경우의 수가 제일 크다

---

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

<br>

현 순열에서 사전 순으로 다음 순열 생성

현재 순열 상태에서 다음으로 큰 순열


배열을 오름차순으로 정렬한 후 시작, 가장 작은 순열에서 시작

아래의 과정을 반복하여 사전순으로 다음으로 큰 순열 생성(가장 큰 내림차순 순열을 만들 때까지 반복)

$nPn$ 만 가능

1. 뒤쪽부터 탐색(가중치가 낮은 자리부터)하여 교환위치(i-1) 찾기(i : 꼭대기)
2. 뒤쪽부터 탐핵하여 교환위치(i-1)와 교환할 큰 값 위치(j)찾기
3. 두 위치 값(i-1, j 교환)
4. 꼭대기위치(i)부터 맨 뒤까지 오름차순 정렬

<br>

NextPermutation 사용 전 숫자배열을 오름차순으로 정렬하여 가장 작은 순열 한 번 처리

<br>

### Next Permutation 을 통한 조합 생성

<br>

원소 크기와 같은 크기의 int 배열 P를 생성

r개의 크기만큼 뒤에서 0이 아닌 값(ex. 1)으로 초기화

nextPermutaion 과정 수행 과정마다 0이 아닌 값의 위치가 변경됨

P 배열에서 0이 아닌 값이 갖고 있는 위치에 해당하는 원소가 조합에 선택된 것

<br><br>

## 부분집합(subset)

<br>

집합에 포함된 원소들을 선택

다수의 중요 알고리즘들이 원소들의 그룹에서 최적의 부분집합을 찾는것

ex) 배낭 짐싸기

<br>

### 부분집합의 수

집합의 원소가 n개 일 때 공집합을 포함하는 부분집합의 수는 $2^n$ 개이다.

이는 각 원소를 부분집합에 포함시키너나 포함시키지 않는 2가지 경우를 모든 원소에 적용한 경우의 수와 같다.

<br>

### 부분집합 생성

각 원소를 부분집합에 포함/비포함의 형태로 재귀적 구현

<br>

```
input[] // 숫자 배열
isSelected[] // 부분집합에 포함/비포함 여부를 저장한 배열

generateSubSet(cnt) // cnt : 현재까지 처리한 원소 개수 

    if(cnt == N)
        부분집합 완성
    else
        isSelected[cnt] = true
        generateSubSet(cnt + 1)
        
        isSelected[cnt] = false
        generateSubSet(cnt + 1)

end generateSubSet()
```