<h2 id="1-미로-찾기-문제를-풀던-중">1. 미로 찾기 문제를 풀던 중</h2>
<p>BFS를 큐로 푸는 것은 익숙했지만, DFS를 재귀와 스택으로 푸는 것은 익숙하지 않음을 체감했다.
코딩테스트에서는 기본적인 DFS에 더해, 백트래킹 시 다양한 변수의 되돌림을 요구한다.. 이를 경험해 봤기 때문에 기초에 대한 탄탄한 정리가 필요했다.</p>
<p><br /> <br /></p>
<h2 id="2-dfs백트래킹">2. DFS(백트래킹)</h2>
<p>DFS(Depth-First Search)와 백트래킹을 이용한 경로 탐색은 트리나 그래프의 모든 가능한 경로를 탐색하는 방법입니다. 이 방법은 문제 해결에 대한 가능한 모든 후보를 검토하고, 목표 상태에 도달하지 못할 경우 그 후보를 배제해 나가는 방식으로, 특히 모든 가능한 선택지를 찾아야 하는 문제에 매우 유용합니다.</p>
<p>아래에서 DFS와 백트래킹을 이용한 경로 탐색을 개념과 예시 코드로 설명하겠습니다.</p>
<h3 id="dfs와-백트래킹-개념"><strong>DFS와 백트래킹 개념</strong></h3>
<ol>
<li><p><strong>DFS (깊이 우선 탐색)</strong>:</p>
<ul>
<li>DFS는 현재의 경로를 따라 최대한 깊숙이 들어간 후, 더 이상 진행할 수 없을 때 다시 뒤로 돌아가는 탐색 방식입니다.</li>
<li>DFS는 스택 자료구조를 사용하며, 재귀를 통해 구현할 수 있습니다.</li>
</ul>
</li>
<li><p><strong>백트래킹 (Backtracking)</strong>:</p>
<ul>
<li>백트래킹은 DFS에서 잘못된 경로를 탐색 중일 때 돌아가는 과정을 말합니다.</li>
<li>일반적으로, 목표에 도달하지 못한 경로를 계속 진행하는 것이 비효율적일 때, 가능한 조합을 가지치기 하는 방식으로 탐색의 효율성을 높이는 기법입니다.</li>
</ul>
</li>
</ol>
<h3 id="경로-탐색-알고리즘"><strong>경로 탐색 알고리즘</strong></h3>
<p>경로 탐색은 시작점에서 끝점까지의 경로를 찾는 문제입니다. 그래프나 트리의 모든 경로를 탐색하여 특정 목표에 도달하는 모든 가능한 경로를 찾습니다.</p>
<p>예를 들어, 다음과 같은 그래프에서 0번 정점에서 시작하여 목표 정점에 도달하는 모든 경로를 탐색한다고 가정합니다.</p>
<ul>
<li><strong>그래프 표현</strong>:<ul>
<li><code>노드 0</code>에서 <code>노드 1</code>과 <code>노드 2</code>로 갈 수 있음.</li>
<li><code>노드 1</code>에서 <code>노드 3</code>으로 갈 수 있음.</li>
<li><code>노드 2</code>에서 <code>노드 3</code>으로 갈 수 있음.</li>
</ul>
</li>
</ul>
<h3 id="c-dfs--백트래킹-코드-예시"><strong>C++ DFS + 백트래킹 코드 예시</strong></h3>
<p>아래는 DFS와 백트래킹을 이용하여 모든 가능한 경로를 탐색하는 예시 코드입니다:</p>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;vector&gt;
using namespace std;

vector&lt;int&gt; path; // 경로를 저장하는 벡터
vector&lt;vector&lt;int&gt;&gt; graph; // 그래프 표현
int target_node; // 목표 정점

void dfs(int current_node) {
    // 현재 노드를 경로에 추가
    path.push_back(current_node);

    // 목표 정점에 도달하면 경로 출력
    if (current_node == target_node) {
        for (int node : path) {
            cout &lt;&lt; node &lt;&lt; &quot; &quot;;
        }
        cout &lt;&lt; endl;
    } else {
        // 현재 노드와 연결된 모든 노드로 탐색 진행
        for (int next_node : graph[current_node]) {
            if (find(path.begin(), path.end(), next_node) == path.end()) { // 이미 방문한 노드 제외
                dfs(next_node);
            }
        }
    }

    // 백트래킹: 탐색이 끝난 노드를 경로에서 제거
    path.pop_back();
}

int main() {
    int num_nodes = 4; // 노드의 개수
    target_node = 3; // 목표 정점 설정

    // 그래프 초기화
    graph.resize(num_nodes);
    graph[0] = {1, 2}; // 0번 노드와 연결된 노드들
    graph[1] = {3};    // 1번 노드와 연결된 노드들
    graph[2] = {3};    // 2번 노드와 연결된 노드들

    cout &lt;&lt; &quot;모든 가능한 경로 탐색:&quot; &lt;&lt; endl;
    dfs(0); // 0번 노드에서 시작하여 DFS 실행

    return 0;
}</code></pre>
<h3 id="코드-설명"><strong>코드 설명</strong></h3>
<ol>
<li><p><strong>그래프 정의 및 DFS 실행</strong>:</p>
<ul>
<li><code>graph</code> 벡터를 이용하여 인접 리스트 형식으로 그래프를 정의합니다.</li>
<li>예제에서는 노드 0에서 시작하여 목표 노드 3까지의 경로를 탐색합니다.</li>
</ul>
</li>
<li><p><strong>DFS 함수</strong> (<code>dfs(int current_node)</code>):</p>
<ul>
<li>현재 노드를 경로 벡터 <code>path</code>에 추가합니다.</li>
<li>만약 목표 노드에 도달하면 현재 경로를 출력합니다.</li>
<li>그렇지 않으면 현재 노드와 연결된 노드를 재귀적으로 탐색합니다.</li>
<li><code>path.pop_back()</code>를 통해 백트래킹 과정에서 이전 노드를 제거하고, 다른 경로를 탐색합니다.</li>
</ul>
</li>
<li><p><strong>백트래킹 사용 이유</strong>:</p>
<ul>
<li>만약 목표 지점에 도달하지 못하고 더 이상 갈 곳이 없을 경우 <code>pop_back()</code>을 통해 한 단계 뒤로 돌아가며 다른 경로를 찾습니다.</li>
<li>이를 통해 이미 탐색한 노드를 제외하고, 새로운 노드를 탐색할 수 있게 됩니다.</li>
</ul>
</li>
</ol>
<h3 id="경로-탐색에서-백트래킹의-장점"><strong>경로 탐색에서 백트래킹의 장점</strong></h3>
<ul>
<li><strong>효율성</strong>: 백트래킹은 목표 노드에 도달하지 않는다면 더 이상 불필요한 탐색을 하지 않고 가지치기를 합니다. 이를 통해 탐색 시간을 줄일 수 있습니다.</li>
<li><strong>모든 경로 탐색</strong>: DFS와 백트래킹을 함께 사용하면 목표 노드에 도달할 수 있는 모든 경로를 찾을 수 있습니다.</li>
<li><strong>메모리 절약</strong>: 백트래킹을 통해 잘못된 경로를 탐색할 경우 빠르게 되돌아가며 불필요한 경로에 대해 메모리를 절약할 수 있습니다.</li>
</ul>
<h3 id="dfs와-백트래킹의-차이점과-유사점"><strong>DFS와 백트래킹의 차이점과 유사점</strong></h3>
<ul>
<li><strong>DFS</strong>는 모든 가능한 깊이로 들어가며 목표를 찾는 과정이지만, <strong>백트래킹</strong>은 가지치기를 통해 비효율적인 탐색을 피하는 기법입니다.</li>
<li><strong>백트래킹</strong>은 <strong>DFS</strong>에서 발생하는 불필요한 탐색을 줄이기 위해 특정 조건이 만족되지 않을 때 되돌아가는 동작을 포함합니다.</li>
</ul>
<h3 id="복잡도"><strong>복잡도</strong></h3>
<ul>
<li><strong>시간 복잡도</strong>: 그래프의 모든 노드를 방문할 수 있기 때문에 시간 복잡도는 <code>O(V + E)</code>입니다. (V는 노드의 개수, E는 간선의 개수)</li>
<li><strong>공간 복잡도</strong>: 재귀 호출로 인해 호출 스택의 깊이가 최악의 경우 <code>O(V)</code>에 이를 수 있습니다.</li>
</ul>
<p>이상으로 DFS와 백트래킹을 사용한 경로 탐색 알고리즘에 대해 설명드렸습니다. 이 방식은 특히 <strong>미로 찾기</strong>나 <strong>최단 경로를 찾지 않아도 되는 모든 경로 탐색 문제</strong>에 매우 유용하게 사용됩니다.</p>