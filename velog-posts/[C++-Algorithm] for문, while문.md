<h2 id="1-for문의-사용-형태">1. for문의 사용 형태</h2>
<p>C++에서 <code>for</code> 문은 크게 세 가지 형태로 사용할 수 있습니다. 각 형태와 용도에 대해 설명드리겠습니다.</p>
<hr />
<h3 id="1-기본-for문">1. <strong>기본 for문</strong></h3>
<pre><code class="language-cpp">for (int i = 0; i &lt; 10; i++) {
    // 반복문 내용
}</code></pre>
<ul>
<li>가장 오래된 형태이며, <strong>초기값, 조건, 증감을 명시적으로 제어</strong></li>
<li>배열, 숫자 범위 등을 순회할 때 주로 사용한다.</li>
</ul>
<h4 id="예시">예시</h4>
<pre><code class="language-cpp">int arr[] = {1, 2, 3, 4, 5};
for (int i = 0; i &lt; 5; i++) {
    cout &lt;&lt; arr[i] &lt;&lt; &quot; &quot;; // 출력: 1 2 3 4 5
}</code></pre>
<hr />
<h3 id="2-범위-기반-for문-range-based-for-loop-c11-이상">2. <strong>범위 기반 for문 (Range-based for loop)</strong> [C++11 이상]</h3>
<pre><code class="language-cpp">for (char c : str) {
    // str 문자열의 각 문자를 c로 순회
}</code></pre>
<ul>
<li>컨테이너(예: <code>std::vector</code>, <code>std::array</code>, <code>std::string</code>)나 배열을 <strong>자동으로 순회</strong></li>
<li>선언된 변수 <code>c</code>는 순회 중 각 요소를 참조</li>
<li>읽기 전용으로 순회하려면 복사본이 생성되고, <strong>수정하려면 참조로 받아야 한다!</strong></li>
</ul>
<h4 id="예시-1">예시</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;vector&gt;
#include &lt;string&gt;

using namespace std;

int main() {
    string str = &quot;Hello&quot;;
    vector&lt;int&gt; nums = {1, 2, 3, 4, 5};

    // 문자열 순회
    for (char c : str) {
        cout &lt;&lt; c &lt;&lt; &quot; &quot;; // 출력: H e l l o
    }
    cout &lt;&lt; endl;

    // 벡터 순회
    for (int num : nums) {
        cout &lt;&lt; num &lt;&lt; &quot; &quot;; // 출력: 1 2 3 4 5
    }
    cout &lt;&lt; endl;

    // 참조로 순회하여 값 수정
    for (int&amp; num : nums) {
        num *= 2;
    }
    for (int num : nums) {
        cout &lt;&lt; num &lt;&lt; &quot; &quot;; // 출력: 2 4 6 8 10
    }
    cout &lt;&lt; endl;

    return 0;
}</code></pre>
<hr />
<h3 id="3-반복자-기반-for문">3. <strong>반복자 기반 for문</strong></h3>
<ul>
<li>C++ STL(예: <code>std::vector</code>, <code>std::list</code>)에서 <strong>반복자를 사용해 순회하는 형태</strong></li>
<li>범위 기반 for문이 등장하기 전에는 이 방법을 주로 사용했습니다.</li>
</ul>
<h4 id="예시-2">예시</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;vector&gt;

using namespace std;

int main() {
    vector&lt;int&gt; nums = {1, 2, 3, 4, 5};

    for (vector&lt;int&gt;::iterator it = nums.begin(); it != nums.end(); ++it) {
        cout &lt;&lt; *it &lt;&lt; &quot; &quot;; // 출력: 1 2 3 4 5
    }
    cout &lt;&lt; endl;

    // 상수 반복자 (읽기 전용)
    for (vector&lt;int&gt;::const_iterator it = nums.cbegin(); it != nums.cend(); ++it) {
        cout &lt;&lt; *it &lt;&lt; &quot; &quot;; // 출력: 1 2 3 4 5
    }

    return 0;
}</code></pre>
<hr />
<h3 id="4-무한-루프">4. <strong>무한 루프</strong></h3>
<ul>
<li>조건 없이 계속 반복합니다. 주로 조건문과 <code>break</code>를 활용해 중간에 종료</li>
<li>while과 유사</li>
</ul>
<h4 id="예시-3">예시</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    int count = 0;

    for (;;) { // 무한 루프
        cout &lt;&lt; &quot;Loop &quot; &lt;&lt; count &lt;&lt; endl;
        if (++count &gt;= 5) break; // count가 5 이상이면 종료
    }

    return 0;
}</code></pre>
<hr />
<h3 id="5-c17-이상의-구조-분해-사용">5. <strong>C++17 이상의 구조 분해 사용</strong></h3>
<ul>
<li>구조 분해(binding)를 활용해 더 복잡한 자료 구조를 순회</li>
</ul>
<h4 id="예시-4">예시</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;map&gt;

using namespace std;

int main() {
    map&lt;string, int&gt; m = {{&quot;Alice&quot;, 30}, {&quot;Bob&quot;, 25}};

    for (const auto&amp; [key, value] : m) {
        cout &lt;&lt; key &lt;&lt; &quot;: &quot; &lt;&lt; value &lt;&lt; endl;
    }

    return 0;
}</code></pre>
<ul>
<li><code>map</code>의 <code>key</code>와 <code>value</code>를 각각 <code>key</code>, <code>value</code> 변수에 바인딩하여 사용할 수 있습니다.</li>
</ul>
<hr />
<h3 id="정리">정리</h3>
<ul>
<li><strong>기본 for문</strong>: 초기값, 조건, 증감 설정이 필요할 때.</li>
<li><strong>범위 기반 for문</strong>: 컨테이너나 배열 순회 시 간결하게 사용.</li>
<li><strong>반복자 기반 for문</strong>: STL 컨테이너에서 세밀한 제어가 필요할 때.</li>
<li><strong>무한 루프</strong>: 종료 조건을 명시적으로 작성해야 할 때.</li>
<li><strong>C++17 구조 분해</strong>: 복잡한 자료 구조를 순회할 때 간결하게 작성.</li>
</ul>
<p><br /> <br /></p>
<h2 id="2-while-문의-사용-형태">2. while 문의 사용 형태</h2>
<p><code>while</code>문은 <strong>조건에 따라 반복 실행</strong>되는 제어문이다. 
<code>for</code>문과는 달리, 반복 횟수를 정하지 않고 조건이 참(<code>true</code>)인 동안 계속 실행되는 특징이 있다. 
아래에 <code>while</code>문의 사용법과 다양한 활용법을 정리해보았다.</p>
<hr />
<h3 id="1-기본-형태">1. <strong>기본 형태</strong></h3>
<pre><code class="language-cpp">while (조건식) {
    // 조건식이 참일 때 실행될 코드
}</code></pre>
<ul>
<li><strong>조건식</strong>: 반복 여부를 결정하는 표현식이다.<ul>
<li>조건식이 <code>true</code>이면 코드 블록을 실행하고, 다시 조건식을 확인.</li>
<li>조건식이 <code>false</code>이면 반복문을 종료.</li>
</ul>
</li>
</ul>
<h4 id="예시-숫자-세기">예시: 숫자 세기</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    int i = 1; // 초기값
    while (i &lt;= 5) { // 조건
        cout &lt;&lt; i &lt;&lt; &quot; &quot;; // 1 2 3 4 5 출력
        i++; // 증감
    }
    return 0;
}</code></pre>
<hr />
<h3 id="2-무한-루프">2. <strong>무한 루프</strong></h3>
<ul>
<li><code>while (true)</code>를 사용하면 조건이 항상 참이므로 <strong>무한히 반복</strong>된다.</li>
<li>종료 조건은 <code>break</code>로 제어.</li>
</ul>
<h4 id="예시-사용자-입력-반복">예시: 사용자 입력 반복</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    while (true) {
        int input;
        cout &lt;&lt; &quot;숫자를 입력하세요 (0 입력 시 종료): &quot;;
        cin &gt;&gt; input;
        if (input == 0) {
            cout &lt;&lt; &quot;프로그램 종료&quot; &lt;&lt; endl;
            break; // 반복문 종료
        }
        cout &lt;&lt; &quot;입력한 숫자: &quot; &lt;&lt; input &lt;&lt; endl;
    }
    return 0;
}</code></pre>
<hr />
<h3 id="3-조건을-나중에-확인하는-do-while문">3. <strong>조건을 나중에 확인하는 <code>do-while</code>문</strong></h3>
<ul>
<li><strong><code>do-while</code>문</strong>은 최소 한 번은 코드 블록을 실행한 뒤 조건을 확인한다.<pre><code class="language-cpp">do {
  // 실행할 코드
} while (조건식);</code></pre>
</li>
</ul>
<h4 id="예시-최소-한-번-실행-보장">예시: 최소 한 번 실행 보장</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    int num;
    do {
        cout &lt;&lt; &quot;양수를 입력하세요: &quot;;
        cin &gt;&gt; num;
    } while (num &lt;= 0); // 조건 확인
    cout &lt;&lt; &quot;입력한 숫자: &quot; &lt;&lt; num &lt;&lt; endl;
    return 0;
}</code></pre>
<hr />
<h3 id="4-while문과-배열-활용">4. <strong><code>while</code>문과 배열 활용</strong></h3>
<ul>
<li><code>while</code>문을 사용해 배열 요소를 순회할 수 있다.</li>
</ul>
<h4 id="예시-배열-합-계산">예시: 배열 합 계산</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int size = sizeof(arr) / sizeof(arr[0]);
    int i = 0, sum = 0;

    while (i &lt; size) {
        sum += arr[i]; // 배열 요소 합산
        i++;
    }

    cout &lt;&lt; &quot;배열의 합: &quot; &lt;&lt; sum &lt;&lt; endl; // 출력: 15
    return 0;
}</code></pre>
<hr />
<h3 id="5-사용자-입력을-조건으로-반복">5. <strong>사용자 입력을 조건으로 반복</strong></h3>
<ul>
<li>사용자 입력에 따라 반복을 제어할 수 있다.</li>
</ul>
<h4 id="예시-입력값이-0이-될-때까지-반복">예시: 입력값이 0이 될 때까지 반복</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    int num = -1;

    while (num != 0) {
        cout &lt;&lt; &quot;0을 입력하면 종료됩니다. 숫자를 입력하세요: &quot;;
        cin &gt;&gt; num;
    }

    cout &lt;&lt; &quot;프로그램 종료&quot; &lt;&lt; endl;
    return 0;
}</code></pre>
<hr />
<h3 id="6-중첩-while문">6. <strong>중첩 <code>while</code>문</strong></h3>
<ul>
<li><code>while</code>문을 중첩하여 2차원 데이터를 처리할 수 있다.</li>
</ul>
<h4 id="예시-2차원-배열-출력">예시: 2차원 배열 출력</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};
    int row = 0;

    while (row &lt; 2) {
        int col = 0;
        while (col &lt; 3) {
            cout &lt;&lt; matrix[row][col] &lt;&lt; &quot; &quot;; // 출력: 1 2 3 4 5 6
            col++;
        }
        cout &lt;&lt; endl;
        row++;
    }

    return 0;
}</code></pre>
<hr />
<h3 id="7-continue와-함께-사용">7. <strong><code>continue</code>와 함께 사용</strong></h3>
<ul>
<li><code>continue</code>를 사용하면 특정 조건에서 나머지 코드를 건너뛰고 다음 반복으로 넘어간다.</li>
</ul>
<h4 id="예시-짝수만-출력">예시: 짝수만 출력</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    int i = 0;
    while (i &lt;= 10) {
        i++;
        if (i % 2 != 0) {
            continue; // 홀수는 건너뜀
        }
        cout &lt;&lt; i &lt;&lt; &quot; &quot;; // 출력: 2 4 6 8 10
    }
    return 0;
}</code></pre>
<hr />
<h3 id="8-while-vs-for">8. <strong><code>while</code> vs <code>for</code></strong></h3>
<ul>
<li><code>while</code>문은 반복 횟수가 <strong>불확실</strong>하거나 조건으로 제어해야 하는 경우 적합하다.</li>
<li><code>for</code>문은 반복 횟수가 <strong>명확</strong>한 경우에 적합하다.</li>
</ul>
<hr />
<h3 id="9-무한-루프-활용-간단한-메뉴-프로그램">9. <strong>무한 루프 활용: 간단한 메뉴 프로그램</strong></h3>
<h4 id="예시-5">예시</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
using namespace std;

int main() {
    while (true) {
        int choice;
        cout &lt;&lt; &quot;1. 메뉴 A\n2. 메뉴 B\n3. 종료\n선택: &quot;;
        cin &gt;&gt; choice;

        if (choice == 1) {
            cout &lt;&lt; &quot;메뉴 A를 선택했습니다.\n&quot;;
        } else if (choice == 2) {
            cout &lt;&lt; &quot;메뉴 B를 선택했습니다.\n&quot;;
        } else if (choice == 3) {
            cout &lt;&lt; &quot;프로그램을 종료합니다.\n&quot;;
            break;
        } else {
            cout &lt;&lt; &quot;잘못된 입력입니다. 다시 시도하세요.\n&quot;;
        }
    }
    return 0;
}</code></pre>
<hr />
<h3 id="정리-1">정리</h3>
<ul>
<li><code>while</code>문은 <strong>조건에 따라 반복</strong>하는 경우 적합하며, 반복 횟수가 사전에 정해지지 않았을 때 주로 사용된다.</li>
<li><strong><code>do-while</code></strong>은 최소 한 번 실행이 보장되는 경우에 사용된다.</li>
<li><code>break</code>와 <code>continue</code>로 제어할 수 있으며, 다양한 형태로 활용할 수 있다.</li>
</ul>