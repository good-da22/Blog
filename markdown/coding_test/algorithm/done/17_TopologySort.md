## 위상 정렬 (Topology Sort)

<br>

유향 그래프의 정점들을 방향을 거스르지 않도록 나열하는 것을 의미

위상 정렬은 순서가 정해져 있는 작업들을 차례대로 수행해야 할 때, 그 순서를 결정해주는 알고리즘

ex) 교육과정의 선수과목 구조

만약 특정 수강 과목에 선수 과목이 있다면 그 선수 과복부터 수강해야하므로, 특정 과목들을 수강해야 할 때 위상 정렬을 통해 올바른 수강 순서를 찾아낼 수 있다.

<br>

선후 관계가 정의된 그래프 구조 상에서 선후 관계에 따라 정렬하기 위해 위상 정렬 이용 가능

정렬 순서는 유향 그래프의 구조에 따라 여러 개의 종류가 나올 수 있다.

위상 정렬이 성립하기 위해서는 반드시 **그래프의 순환이 존재하니 않아야 한다.**

그래프가 **비순환 유향 그래프(directed acyclic graph)**여야 한다.

<br>

### 위상 정렬 구현 - BFS 사용

<br>

1. 진입 차수가 0인 노드(시작점)를 큐에 모두 넣는다.
2. 큐에서 진입 차수가 0인 노드를 꺼내어 사진솨 인접한 노드의 간선을 제거한다.
    - 인접한 노드의 진입 차수를 1 감소시킨다.
3. 간선 제거 후 진입 차수가 0이 된 노드를 큐에 넣는다.
4. 큐가 공백 큐가 될 때까지 2-3 작업을 반복
    - 모든 노드가 다 처리되었다면 위상 정렬 완성
    - 모든 노드가 처리되지 않았다면 사이클링 발생