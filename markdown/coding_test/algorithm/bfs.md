## 너비 우선 탐색(Breadth First Search, BFS)

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