## 너비 우선 탐색(Breadth First Search, BFS)

<br>

비선형 자료구조를 완전탐색

너비 - 루트에서 자신까지 오는 간선 수 (각 노드에서의 높이), 높이가 낮은 순서에서 높은 순서로

너비 우선 탐색은 루트 노드의 자식도드를 먼저 모두 차례로 방문한 후, 방문했던 자식 노드들을 기준으로 하여 다시 해당 노드의 자식 노드들을 차례로 방문하는 방식

인접한 노드들에 대해 탐색 후, 차례로 다시 너비우선탐색을 진행해야 하므로, 선입선출 형태의 자료구조인 큐를 활용

<br>

```
BFS()
    큐 생성
    루트 v를 큐에 삽입

    while(큐가 비어 있지 않은 경우) {
        t <- 큐의 첫 번째 원소 반환
        t 방문

        for(t와 연결된 모든 간선에 대해) {
            u <- t의 자식 노드
            u 를 큐에 삽입
        }
    }

end BFS()
```

<br><br>

## 깊이 우선 탐색(Depth First Search, DFS)

<br>

루트 노드에서 출발하여, 한 방뱡으로 갈 수 있는 경로가 있는 곳까지 깊이 탐색해 가다가 어 이상 갈 곳이 없게 되면, 가장 마지막에 만났던 갈림길 간선이 있는 노드로 되돌아와서 다른 방뱡의 노드로 탐색을 계속 반복하여 결국 모든 노드를 방문하는 순회 방법

가장 마지막에 만났던 갈림길의 노드로 되돌아가서 다시 깊이 우선 탐색을 반복해야 하므로 재귀적으로 구현하거나 후입선출 구조의 스택 사용해서 구현

<br>

```
DFS(v) // 매개변수 v, 탐색 방향을 바꾸는 결정적 요인

    v 방문;

    for(v의 모든 자식노드 w){    // 자신의 자식을 탐색하는 방법은 동일, 재귀 사용
        DFS(w);                 // 자식이 없으면 재귀 유도가 되지 않는다, 기저조건
    }

end DFS()
```

<br><br>

## 순회(traversal)

<br>

트리의 노드들을 체계적으로 방문하는 것

3가지 기본적인 순회방법
- 전위 순회(preorder traversal) : VLR
  - 부모노드 방문 후, 자식노드를 좌, 우 순서로 방문

- 중위 순회(inorder traversal) : LVR
  - 왼쪽 자식노드, 부모노드, 오른쪽 자식노드 순으로 방문

- 후위 순회(postorder traversal) : LRV
  - 자식노드를 좌우 순서로 방문한 후, 부모노드로 방문

<br>

### 전위 순회(preorder traversal)

<br>

1. 현재 노드 T를 방문하여 처리 -> V
2. 현재 노드 T의 왼쪽 서브트리로 이동 -> L
3. 현재 노드 T의 오른쪽 서브트리로 이동 -> R

<br>

```
preorder_traverse(T)

    if (T is not null)

        visit(T)
        preorder_traverse(T.left)
        preorder_traverse(T.right)
    
end preorder_traverse
```

<br>

### 중위 순회(inorder traversal)

<br>

1. 현재 노드 T의 왼쪽 서브트리로 이동 -> L
2. 현재 노드 T를 방문하여 처리 -> V
3. 현재 노드 T의 오른쪽 서브트리로 이동 -> R

<br>

```
inorder_traverse(T)

    if (T is not null)

        inorder_traverse(T.left)
        visit(T)
        inorder_traverse(T.right)

end inorder_traverse
```

<br>

### 후위 순회(postorder traversal)

<br>

1. 현재 노드 T의 왼쪽 서브트리로 이동 -> L
2. 현재 노드 T의 오른쪽 서브트리로 이동 -> R
3. 현재 노드 T를 방문하여 처리 -> V

<br>

```
postorder_traverse(T)

    if (T is not null)

        postorder_traverse(T.left)
        
        postorder_traverse(T.right)
        visit(T)

end postorder_traverse
```