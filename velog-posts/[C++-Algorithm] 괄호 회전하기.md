<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/33a31513-1b19-416b-b99d-40caaf94e49c/image.png" /></p>
<h2 id="문제-설명">문제 설명</h2>
<p>다음 규칙을 지키는 문자열을 올바른 괄호 문자열이라고 정의합니다.</p>
<p>(), [], {} 는 모두 올바른 괄호 문자열입니다.
만약 A가 올바른 괄호 문자열이라면, (A), [A], {A} 도 올바른 괄호 문자열입니다. 예를 들어, [] 가 올바른 괄호 문자열이므로, ([]) 도 올바른 괄호 문자열입니다.
만약 A, B가 올바른 괄호 문자열이라면, AB 도 올바른 괄호 문자열입니다. 예를 들어, {} 와 ([]) 가 올바른 괄호 문자열이므로, {}([]) 도 올바른 괄호 문자열입니다.
대괄호, 중괄호, 그리고 소괄호로 이루어진 문자열 s가 매개변수로 주어집니다. 이 s를 왼쪽으로 x (0 ≤ x &lt; (s의 길이)) 칸만큼 회전시켰을 때 s가 올바른 괄호 문자열이 되게 하는 x의 개수를 return 하도록 solution 함수를 완성해주세요.</p>
<h2 id="풀이">풀이</h2>
<h3 id="사고과정">사고과정</h3>
<ol>
<li>일단 구현할 로직을 크게 두 분류로 나누어 생각해야 한다.<ul>
<li>올바른 괄호 문자인지 판단하는 로직<ul>
<li>괄호 짝을 지우는 로직</li>
</ul>
</li>
<li>괄호 문자를 회전시키는 로직</li>
</ul>
</li>
<li>로직의 구성은 다음과 같이 생각되었다.<ol>
<li>반복문으로 문자열 크기만큼 수행<ol start="2">
<li>회전</li>
<li>올바른 괄호 문자이면 answer에 1 추가</li>
</ol>
</li>
<li>answer 반환</li>
</ol>
</li>
</ol>
<h3 id="주의해야-할-점">주의해야 할 점</h3>
<ol>
<li>구현 과정에서 stack 구현 시 자료형을 뒤에 붙이는 걸 깜빡했다..<pre><code class="language-cpp">stack&lt;char&gt; st; // 이렇게 구현해야 했는데
stack st; // 이렇게 구현하고 왜 안되지? 이러고 있었다.</code></pre>
</li>
<li>그리고 구현할 때, 회전시키는 rotate함수 구현에는 다양한 방법이 있겠지만 챗지피티에서는 s.substr(1) + s[0];을 추천해줬다.<pre><code class="language-cpp">s.substr(1)// s의 1번째 위치부터 끝까지 복사</code></pre>
그 외에는 문제점은 크게 없었다.</li>
</ol>
<h3 id="코드">코드</h3>
<pre><code class="language-cpp">#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;stack&gt;
#include &lt;algorithm&gt;

using namespace std;
/*
1. 올바른 괄호 문자인지 판단하는 로직 + 모든 경우 회전시키는 로직
2. 올바른 괄호 문자 판단 &lt;- 스택으로 구현
  2-1. 
*/
bool del_set(char a, char b){
    if (a == '(' &amp;&amp; b == ')') return true;
    else if (a == '[' &amp;&amp; b == ']') return true;
    else if (a == '{' &amp;&amp; b == '}') return true;
    else return false;
}

bool cor_set(string s){
    stack&lt;char&gt; st;
    for (int i = 0; i &lt; s.size(); i++){
        if (st.empty()) st.push(s[i]);
        else{
            if (del_set(st.top(), s[i])) st.pop();
            else st.push(s[i]);
        }
    }
    return st.empty();
}

string rotate(string s){
    return s.substr(1) + s[0];
}

int solution(string s) {
    int answer = 0;
    for (int i = 0; i &lt; s.size(); i++){
        s = rotate(s);
        if (cor_set(s)) answer ++;
    }
    return answer;
}</code></pre>