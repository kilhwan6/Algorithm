<h3 id="1-stringfind는">1. String::find()는..</h3>
<p>C++에서 문자열 내의 특정 문자, 혹은 문자열의 첫 번째 발생 위치를 찾는 데 사용된다. 여러 번 등장하더라도 가장 먼저 등장하는 위치만 반환되기 때문에, 여러 개의 대상을 찾아낼 때 어떻게 응용되는지 구현해보았다.
<br /><br /></p>
<h3 id="2-find-메소드의-동작">2. find() 메소드의 동작</h3>
<h4 id="함수-정의">함수 정의</h4>
<pre><code class="language-cpp">size_t find(const string&amp; str, size_t pos = 0) const;
size_t find(const char* s, size_t pos = 0) const;
size_t find(char c, size_t pos = 0) const;</code></pre>
<ul>
<li>str 또는 s: 찾고자 하는 문자열 또는 문자입니다.</li>
<li>pos: 검색을 시작할 위치 (기본값은 0).
반환값</li>
<li>찾았을 경우: 문자열 내에서 찾은 첫 번째 위치의 인덱스(size_t)를 반환합니다.</li>
<li>찾지 못했을 경우: string::npos를 반환합니다.</li>
</ul>
<h4 id="예제">예제</h4>
<h5 id="문자-검색">문자 검색</h5>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;string&gt;

using namespace std;

int main() {
    string text = &quot;Hello, World! Hello, Universe!&quot;;

    size_t pos = text.find('o');  // 'o'를 찾음
    cout &lt;&lt; &quot;First 'o': &quot; &lt;&lt; pos &lt;&lt; endl;  // 출력: 4

    pos = text.find('o', pos + 1);  // 다음 'o'를 찾음
    cout &lt;&lt; &quot;Second 'o': &quot; &lt;&lt; pos &lt;&lt; endl;  // 출력: 8

    return 0;
}</code></pre>
<h5 id="문자열-검색">문자열 검색</h5>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;string&gt;

using namespace std;

int main() {
    string text = &quot;abc abc abc&quot;;

    size_t pos = text.find(&quot;abc&quot;);  // &quot;abc&quot;를 찾음
    cout &lt;&lt; &quot;First 'abc': &quot; &lt;&lt; pos &lt;&lt; endl;  // 출력: 0

    pos = text.find(&quot;abc&quot;, pos + 1);  // 다음 &quot;abc&quot;를 찾음
    cout &lt;&lt; &quot;Second 'abc': &quot; &lt;&lt; pos &lt;&lt; endl;  // 출력: 4

    return 0;
}
</code></pre>
<p><br /><br /></p>
<h3 id="3-찾는-문자열이-여러-개일-경우">3. 찾는 문자열이 여러 개일 경우</h3>
<p>find()는 하나의 문자나 문자열만 처리할 수 있으므로, 여러 문자를 동시에 찾으려면 다른 방법을 사용해야 한다. 
<strong>for 또는 std::find_first_of</strong>를 사용한다.</p>
<h4 id="여러-문자-중-첫-번째로-등장하는-위치-찾기">여러 문자 중 첫 번째로 등장하는 위치 찾기</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;string&gt;

using namespace std;

int main() {
    string text = &quot;apple pie and banana&quot;;
    string chars = &quot;aeiou&quot;;  // 모음

    size_t pos = text.find_first_of(chars);
    cout &lt;&lt; &quot;First vowel: &quot; &lt;&lt; text[pos] &lt;&lt; &quot; at position &quot; &lt;&lt; pos &lt;&lt; endl;

    return 0;
}</code></pre>
<h4 id="출력">출력</h4>
<pre><code class="language-cpp">First vowel: a at position 0</code></pre>
<p><br /><br /></p>
<h3 id="4-결과">4. 결과</h3>
<ol>
<li><p>*<em>string::find()는 첫 번째로 등장한 위치만 반환합니다. *</em></p>
<ul>
<li>동일한 문자나 문자열이 여러 번 등장하더라도, 가장 앞에 있는 것만 반환.</li>
</ul>
</li>
<li><p><strong>여러 번 등장한 경우</strong></p>
<ul>
<li>다음 위치를 찾으려면 pos를 조정하여 반복적으로 호출.</li>
</ul>
</li>
<li><p><strong>여러 문자나 문자열 중 하나를 찾으려면:</strong></p>
<ul>
<li>find_first_of를 사용하거나, 반복문으로 각 문자를 개별적으로 찾는 방식으로 구현.
<br /><br /><h3 id="5-stdfind_first_of">5. std::find_first_of</h3>
std::find_first_of는 C++ 표준 라이브러리의  헤더에 포함된 알고리즘으로, 주어진 범위에서 특정 요소들 중 첫 번째로 나타나는 요소를 찾는 함수입니다.</li>
</ul>
</li>
</ol>
<p>이 함수는 두 범위를 비교하여, 첫 번째 범위에서 두 번째 범위에 포함된 요소가 발견되면 해당 위치의 <strong>반복자(iterator)</strong>를 반환합니다.</p>
<pre><code class="language-cpp">template&lt;class InputIterator, class ForwardIterator&gt;
InputIterator find_first_of(InputIterator first1, InputIterator last1,
                            ForwardIterator first2, ForwardIterator last2);

template&lt;class InputIterator, class ForwardIterator, class BinaryPredicate&gt;
InputIterator find_first_of(InputIterator first1, InputIterator last1,
                            ForwardIterator first2, ForwardIterator last2,
                            BinaryPredicate p);</code></pre>
<h4 id="매개변수">매개변수</h4>
<ol>
<li>first1, last1: 첫 번째 범위 (검색할 대상).</li>
<li>first2, last2: 두 번째 범위 (찾으려는 요소들).</li>
<li>p (선택적): 요소 비교를 위한 사용자 정의 Binary Predicate 함수(참/거짓 반환).</li>
</ol>
<h4 id="반환값">반환값</h4>
<ul>
<li><strong>첫 번째 범위에서 두 번째 범위의 요소 중 하나를 찾은 위치의 반복자(iterator)</strong>를 반환합니다.</li>
<li>찾지 못하면 첫 번째 범위의 끝(last1)을 반환합니다.</li>
</ul>
<h4 id="작동-방식">작동 방식</h4>
<ol>
<li>첫 번째 범위 ([first1, last1))의 각 요소를 순차적으로 검사합니다.</li>
<li>각 요소가 두 번째 범위 ([first2, last2))에 포함되어 있는지 확인합니다.</li>
<li>포함되어 있다면 해당 요소의 반복자를 반환합니다.
<br /><br /><br /><br /><h4 id="사용-예시">사용 예시</h4>
<h4 id="1-기본-사용">1. 기본 사용</h4>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;
</code></pre>
</li>
</ol>
<p>using namespace std;</p>
<p>int main() {
    vector v1 = {1, 2, 3, 4, 5};
    vector v2 = {4, 6, 7};  // 찾으려는 값들</p>
<pre><code>// 첫 번째 범위에서 두 번째 범위의 첫 번째 값을 찾음
auto it = find_first_of(v1.begin(), v1.end(), v2.begin(), v2.end());

if (it != v1.end()) {
    cout &lt;&lt; &quot;First matching element: &quot; &lt;&lt; *it &lt;&lt; endl; // 출력: 4
} else {
    cout &lt;&lt; &quot;No matching element found!&quot; &lt;&lt; endl;
}

return 0;</code></pre><p>}</p>
<pre><code>#### 출력:
```cpp
First matching element: 4</code></pre><p>  <br /><br /></p>
<h4 id="2-사용자-정의-비교-함수">2. 사용자 정의 비교 함수</h4>
<p>find_first_of에 <strong>Binary Predicate</strong>를 제공하면, 사용자 정의 조건을 기준으로 값을 찾을 수 있습니다.</p>
<pre><code class="language-cpp">  #include &lt;iostream&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;
#include &lt;cctype&gt; // for ::tolower

using namespace std;

// 대소문자 무시 비교 함수
bool case_insensitive_compare(char a, char b) {
    return tolower(a) == tolower(b);
}

int main() {
    string str1 = &quot;Hello, World!&quot;;
    string str2 = &quot;ow&quot;;

    // 대소문자를 무시하고 검색
    auto it = find_first_of(str1.begin(), str1.end(),
                            str2.begin(), str2.end(),
                            case_insensitive_compare);

    if (it != str1.end()) {
        cout &lt;&lt; &quot;First matching character: &quot; &lt;&lt; *it &lt;&lt; endl; // 출력: o
    } else {
        cout &lt;&lt; &quot;No matching character found!&quot; &lt;&lt; endl;
    }

    return 0;
}</code></pre>
<h4 id="출력-1">출력:</h4>
<pre><code class="language-cpp">First matching character: o</code></pre>