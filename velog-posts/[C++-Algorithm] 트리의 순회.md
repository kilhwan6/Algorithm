<h2 id="1-swea-1231-중위순회">1. SWEA 1231 중위순회</h2>
<p>문제를 풀기 위해서 기초적으로 갖춰야 하는 지식이다.</p>
<h3 id="문제-내용">문제 내용</h3>
<p>※ SW Expert 아카데미의 문제를 무단 복제하는 것을 금지합니다.</p>
<p>주어진 트리를 in-order 형식으로 순회해 각 노드를 읽으면 특정 단어를 알 수 있다.</p>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/10ac04cf-031c-4a71-b1ea-c99659a63ed9/image.png" /></p>
<p>위 트리를 in-order 형식으로 순회할 경우 SOFTWARE 라는 단어를 읽을 수 있다.
주어진 트리를 in-order 형식으로 순회했을때 나오는 단어를 출력하라.</p>
<h3 id="원리">원리</h3>
<p>즉, 문제를 풀기 위해서는 다음과 같은 순서로 읽어나가야 한다.
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/ede8e547-d524-4f7a-87d6-0b95e1b7dca8/image.png" /></p>
<ol>
<li>왼쪽 서브 트리를 탐색한다.</li>
<li>루트 노드를 탐색한다.</li>
<li>오른쪽 서브 트리를 탐색한다.</li>
</ol>
<p>위의 순서를 재귀함수로 구현하면 되는 것..!
코드 형식으로 한 번 보자.
코드는 Chat gpt4 with canvas를 이용하였다. ㅎㅎ</p>
<pre><code class="language-cpp">void inorderTraversal(Node* node) {
    if (node == nullptr)
        return;
    inorderTraversal(node-&gt;left); // 왼쪽 서브트리 방문
    cout &lt;&lt; node-&gt;data &lt;&lt; &quot; &quot;; // 루트 노드 방문
    inorderTraversal(node-&gt;right); // 오른쪽 서브트리 방문
}</code></pre>
<h3 id="풀이">풀이</h3>
<p>그렇다면 Input단에서부터 확인해 보아요.</p>
<h4 id="1input">1.Input</h4>
<pre><code class="language-cpp">void input() {
    cin &gt;&gt; N;
    v.resize(N + 1);           // 노드 번호가 1부터 시작하므로 N+1 크기로 벡터 생성
    map.resize(N + 1, { 0, 0 }); // 좌우 자식 정보도 N+1 크기로 생성하여 0으로 초기화

    int a, c, d;
    char b;
    //N이 짝수, 홀수냐에 따라 달라짐
    for (int i = 0; i &lt; N; i++) {
        cin &gt;&gt; a &gt;&gt; b;
        v[a] = b;

        if (2 * a &lt;= N) { // 자식이 있는 노드들만 처리 (정점이 2*a로 갈 수 있는지 확인)
            cin &gt;&gt; c;
            map[a].first = c;
            if (2 * a + 1 &lt;= N) { // 오른쪽 자식도 있는 경우
                cin &gt;&gt; d;
                map[a].second = d;
            }
        }
    }
}</code></pre>
<h4 id="2-func">2. func</h4>
<pre><code class="language-cpp">void search(int node) {
    if (node == 0) return; // 노드가 0인 경우 탐색 종료 (자식이 없다는 의미)
    // 좌측 트리 탐색
    search(map[node].first);
    // 현재 노드 탐색
    result += v[node];
    // 우측 트리 탐색
    search(map[node].second);
}

void func() {
    search(1);
}</code></pre>
<p><br /> <br /></p>
<h2 id="2-이진트리의-순회">2. 이진트리의 순회</h2>
<p>이진 트리의 순회 방법에는 전위 순회(Preorder Traversal), 중위 순회(Inorder Traversal), 후위 순회(Postorder Traversal)의 세 가지가 있습니다. 각 방법은 노드를 방문하는 순서에 따라 구분되며, C++로 구현할 수 있습니다.</p>
<p><strong>1. 전위 순회 (Preorder Traversal)</strong></p>
<p>전위 순회는 루트 노드를 먼저 방문한 후, 왼쪽 자식 노드, 오른쪽 자식 노드의 순서로 방문합니다.</p>
<ul>
<li>순회 순서: 루트 → 왼쪽 서브트리 → 오른쪽 서브트리</li>
</ul>
<pre><code class="language-cpp">void preorderTraversal(Node* node) {
    if (node == nullptr)
        return;
    cout &lt;&lt; node-&gt;data &lt;&lt; &quot; &quot;; // 루트 노드 방문
    preorderTraversal(node-&gt;left); // 왼쪽 서브트리 방문
    preorderTraversal(node-&gt;right); // 오른쪽 서브트리 방문
}</code></pre>
<p><strong>2. 중위 순회 (Inorder Traversal)</strong></p>
<p>중위 순회는 왼쪽 자식 노드를 먼저 방문하고, 그 다음에 루트 노드를 방문하며, 마지막으로 오른쪽 자식 노드를 방문합니다.</p>
<ul>
<li>순회 순서: 왼쪽 서브트리 → 루트 → 오른쪽 서브트리</li>
</ul>
<pre><code class="language-cpp">void inorderTraversal(Node* node) {
    if (node == nullptr)
        return;
    inorderTraversal(node-&gt;left); // 왼쪽 서브트리 방문
    cout &lt;&lt; node-&gt;data &lt;&lt; &quot; &quot;; // 루트 노드 방문
    inorderTraversal(node-&gt;right); // 오른쪽 서브트리 방문
}</code></pre>
<p><strong>3. 후위 순회 (Postorder Traversal)</strong></p>
<p>후위 순회는 왼쪽 자식 노드와 오른쪽 자식 노드를 먼저 방문한 후, 마지막에 루트 노드를 방문합니다.</p>
<ul>
<li>순회 순서: 왼쪽 서브트리 → 오른쪽 서브트리 → 루트</li>
</ul>
<pre><code class="language-cpp">void postorderTraversal(Node* node) {
    if (node == nullptr)
        return;
    postorderTraversal(node-&gt;left); // 왼쪽 서브트리 방문
    postorderTraversal(node-&gt;right); // 오른쪽 서브트리 방문
    cout &lt;&lt; node-&gt;data &lt;&lt; &quot; &quot;; // 루트 노드 방문
}</code></pre>
<p>이러한 순회 방법을 통해 이진 트리의 모든 노드를 체계적으로 방문할 수 있습니다. 각 순회 방법은 특정한 문제 해결에 유용하게 활용될 수 있습니다.</p>
<p>아래 이미지는 각 순회 방법의 방문 순서를 시각적으로 나타낸 것입니다.</p>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/1738ecbb-5ec7-4098-a7ad-5b362bdae97d/image.png" /></p>