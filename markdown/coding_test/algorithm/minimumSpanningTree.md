## 최소 신장 트리



최소 신장 트리 - N 개 정점을 가진 그래프에서 N개의 정점을 모두 연결하기 위해 N-1 개 간선을 선택하여 만든 트리

무향 그래프, 가중치를 가진 그래프에서 만들 수 있다.

## Krusakal 알고리즘

간전 중심 표현 그래프

간선 리스트 사용




## Prim 알고리즘

정점 중심 표현 그래프

<br>

**하나의 정점에서 연결된 간선들 중에 하나씩 선택하면서 MST를 만들어 가는 방식**

<br>

1. 임의 정점 하나를 선택해서 시작
2. 선택한 정점과 인접한 정점들 중 최소 비용의 간선이 존재하는 정점을 선택
3. 모든 정점이 선택될 때 까지 1, 2 과정 반복

<br>

**서로소인 2개의 집합(2 disjoint-sets) 정보를 유지**

<br>

- 트리 정점(tree vertuces) - MST를 만들기 위해 선택된 정점들
- 비트리 정점들(non-tree vertices) - 선택되지 않은 정점들

<br>

### 의사코드

<br>

```
MST-PRIM(G, r)                           
    // G : 그래프. r : 시작 정점, minEdge[] : 각 정점 기준으로 타 정점과의 최소 간선 비용

    // result: MST비용, cnt : 처리한 정점수, visited[] : MST에 포함된 정점 여부
    result <- 0, cnt <- 0               
    FOR u in G.V
        minEdge[u] <- MAX_VALUE
    minEdge[r] <- 0                     // 시작 정점 r의 최소비용 0 처리

    WHILE true

        // 방문하지 않은(MST에 포함되지 않은 정점) 최소 비용 정점 찾기
        u <- Extract-MIN()
                      
        visited[u] <- true              // 방문 처리
        result <- result + minEdge[u]   // 비용 누적
        if(++cnt == N) break            // 모든 정점이 다 연결되었으면 MST 완성
        FOR v int G.Adj[u]              // u의 인접 정점들

            // u -> v 비용이 v의 최소비용보다 작다면
            IF visited[v] == false AND w(u, v) < minEdge[v] 
                minEdge[v] <- w(u, v)
    return result
end MST-PRIM
```