## 최소 신장 트리 (Minimum Spanning Tree)

<br>

**신장 트리** - n개의 정점으로 이루어진 무향 그래프에서 n개의 정점과 n-1개의 간선으로 이루어진 트리

**최소 신장 트리** -무향 가중치 그래프에서 신장 트리를 구성하는 간선들의 가중치의 합이 최소인 신장 트리

무향 그래프, 가중치를 가진 그래프에서 만들 수 있다.

### Krusakal 알고리즘

<br>

간선을 하나씩 선택해서 **MST**를 찾는 알고리즘

간전 중심 표현 그래프

간선 리스트 사용

1. 최초, 모든 간선을 가중치에 따라 **오름차순**dmfh wjdfuf
2. 가중치가 가장 낮은 간선부터 선택하면서 트리를 증가
    - 사이클이 존재하면 다음으로 가중치가 낮은 간선 선택
3. n-1개의 간선이 선택될 때까지 2를 반복

<br>

```
// G.V : 그래프의 정점 집합
// G.E : 그래프의 간선 집합

MST-KRUSKAL(G, w)
    FOR vertext v in G.V
        Make-Set(v)
    
    G.E에 포함된 간선들을 가중치 w를 이용한 오름차순 정렬

    FOR 가중치가 가장 낮은 간선(u, v) n-1개 선택
        IF Find-Set(u) != Find-Set(v)
            Union(u, v)
```

<br>

### Prim 알고리즘

<br>

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