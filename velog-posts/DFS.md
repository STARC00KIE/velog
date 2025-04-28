<h1 id="깊이-우선-탐색dfs으로-모든-그래프의-노드를-순회하는-함수">깊이 우선 탐색(DFS)으로 모든 그래프의 노드를 순회하는 함수</h1>
<pre><code class="language-python">from collections import defaultdict

def solution(graph, start):
    # 그래프를 인접 리스트로 변환
    adj_list = defaultdict(list)
    for u, v in graph:
        adj_list[u].append(v) # 인접 리스트

    print(f'adj_list: {adj_list}')
    # DFS 탐색 함수
    def dfs(node, visited, result):
        visited.add(node) # 현재 노드를 방문한 노드들의 집합에 추가
        result.append(node) # 현재 노드를 결과 리스트에 추가
        # node에 해당하는 이웃 노드들의 리스트를 거져옴, node가 dict에 없을 때 빈 리스트([])를 반환함
        for neighbor in adj_list.get(node, []): # 현재 노드와 인접한 노드 순회
            if neighbor not in visited: # 아직 방문하지 않은 노드라면
                dfs(neighbor, visited, result) # 탐색 함수 실행

    # DFS를 순회한 결과를 반환
    visited = set()
    result = []
    dfs(start, visited, result)
    return result

sol1 = solution([['A', 'B'], ['B', 'C'], ['C', 'D'], ['D', 'E']], 'A')
sol2 = solution([['A', 'B'], ['A', 'C'], ['B', 'D'], ['B', 'E'], ['C', 'F'], ['E', 'F']], 'A')

print(sol1)
print(sol2)</code></pre>