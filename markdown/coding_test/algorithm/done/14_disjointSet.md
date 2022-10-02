## 서로소 집합(Disjoint Set)

<br>

서로소 또는 상호배타 집합들은 서로 중복 포함된 원소가 없는 집합들

다시 말해 교집합이 없다.

집합에 속한 하나의 특정 멤버를 통해 각 집합들을 구분, 이를 **대표자(representative)**라 한다.

**서로소 집합을 표현하는 방법** - 집합 구성요소(원소) 표현
- 연결 리스트
- 트리

**서로소 집합 연산**
- Make-set(x) : 집합 생성(x원소(대표자)를 가지는)
- Find-set(x) : x가 속한 집합 찾기
- Union(x, y) : x와 y 원소를 하나의 집합으로 만들기 (대표자끼리 합친다)

<br>

### 서로소 집합 표현 - 연결 리스트

<br>

같은 집합의 원소들은 하나의 연결리스트로 관리한다.

연결리스트의 맨 앞의 원소를 집합의 대표 원소로 삼는다.

각 원소는 집합의 대표원소를 가리키는 **링크**를 갖는다.

<br>

### 서로소 집합 표현 - 트리

<br>

같은 집합의 원소들을 하나의 트리로 표현한다.

자식 노드가 부모 노드를 가리키며 루트 노드가 대표자가 된다.

<br>

### 서로소 집합 연산 - Make-Set(x)

<br>

유일한 멤버 x를 포함하는 새로운 집합을 생성하는 연산

```
Make-set(x)
    p[x] = x
```

<br>

### 서로소 집합 연산 - Find-Set(x)

<br>

x를 포함하는 집합을 찾는 연산

```
Find-Set(x)
    if x == p[x]
        return x
    else
        returb Find-Set(p[x])
```

<br>

### 서로소 집합 연산 - Union(x, y)

<br>

x와 y를 포함하는 두 집합을 통합하는 연산

```
Union(x, y)
    if Find-Set(y) == Find-Set(x)
        return
    p[Finde-Set(y)] = Find-Set(x)
```

<br>

#### 연산의 효율을 높이는 방법

<br>

Rank를 이용한 Union
- 각 노드는 자신을 루트로 하는 subtree의 높이를 rank로 저장
- 두 집합을 합칠 때 rank가 낮은 집합을 rank가 높은 집합에 붙인다.

Path compression
- Find-Set을 행하는 과정에서 만나는 모든 노드들이 직접 root를 가리키도록 포인터를 바꾸어 준다.
- 특정 노드에서 루트까지의 경로를 찾아 가면서 노드의 부모 정보를 갱신

```
Find-Set(x)
    if x == p[x]
        return x
    else
        returb p[x] = Find-Set(p[x])
```