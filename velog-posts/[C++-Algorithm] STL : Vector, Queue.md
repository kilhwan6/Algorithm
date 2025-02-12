<h3 id="1swea-암호문-암호생성기-문제를-풀며">1.SWEA 암호문, 암호생성기 문제를 풀며</h3>
<p>자료구조를 사용하면 수월하게 풀 수 있음을 알아차리고 기존에 사용하던 자료구조 메소드들을 다시 기억해보는 시간을 갖도록 해야겠습니다.
<br /><br /></p>
<h3 id="2-vector란">2. Vector란?</h3>
<p>배열과 똑같은 사용법. 
메모리 heap에 생성해 동적할당하며 배열보단 속도가 느리다.
하지만 메모리를 효율적으로 관리하고 예외처리가 쉬움.
<br /><br /></p>
<h4 id="vector의-초기화">Vector의 초기화</h4>
<table>
<thead>
<tr>
<th>Method</th>
<th>기능</th>
</tr>
</thead>
<tbody><tr>
<td>vector&lt;자료형&gt; 변수명</td>
<td>백터 생성</td>
</tr>
<tr>
<td>vector&lt;자료형&gt; 변수명(숫자)</td>
<td>숫자만큼 백터 생성 후 0으로 초기화</td>
</tr>
<tr>
<td>vector&lt;자료형&gt; 변수명 = { 변수1, 변수2, 변수3... }</td>
<td>백터 생성 후 오른쪽 변수 값으로 초기화</td>
</tr>
<tr>
<td>vector&lt;자료형&gt; 변수명[] = {, }</td>
<td>백터 배열(2차원 백터)선언 및 초기화(열은 고정, 행은 가변)</td>
</tr>
<tr>
<td>vector&lt;vector&lt;자료형&gt;&gt; 변수명</td>
<td>2차원 백터 생성(열과 행 모두 가변)</td>
</tr>
<tr>
<td>vector&lt;자료형&gt;변수명.assign(범위, 초기화할 값)</td>
<td>백터의 범위 내에서 해당 값으로 초기화</td>
</tr>
<tr>
<td><br /><br /></td>
<td></td>
</tr>
<tr>
<td>#### Vector의 Iterators</td>
<td></td>
</tr>
<tr>
<td>Method</td>
<td>기능</td>
</tr>
<tr>
<td>---</td>
<td>---</td>
</tr>
<tr>
<td>v.begin()</td>
<td>백터 시작점의 주소 값 반환</td>
</tr>
<tr>
<td>v.end()</td>
<td>백터 (끝부분 + 1) 주소값 반환</td>
</tr>
<tr>
<td>v.rbegin() (revers begin)</td>
<td>백터의 끝 지점을 시작점으로 반환</td>
</tr>
<tr>
<td>v.rend() (revers end)</td>
<td>백터의 (시작 + 1) 지점을 끝 부분으로 반환</td>
</tr>
<tr>
<td>##### begin(), end() 그림</td>
<td></td>
</tr>
<tr>
<td><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/0d4e40da-7714-4acc-bfdc-5d11823cc714/image.png" /></td>
<td></td>
</tr>
<tr>
<td>##### rbegin(), rend() 그림</td>
<td></td>
</tr>
<tr>
<td><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/22c17b73-4a4a-4b3f-90c9-71aaa93d8d16/image.png" /></td>
<td></td>
</tr>
<tr>
<td><br /><br /></td>
<td></td>
</tr>
<tr>
<td>#### Vector Element access(백터의 요소 접근)</td>
<td></td>
</tr>
</tbody></table>
<table>
<thead>
<tr>
<th>Method</th>
<th>기능</th>
</tr>
</thead>
<tbody><tr>
<td>v.at(i)</td>
<td>백터의 i번째 요소 접근 (범위 검사함)</td>
</tr>
<tr>
<td>v.[i] (operator [])</td>
<td>백터의 i번째 요소 접근 (범위 검사 안함)</td>
</tr>
<tr>
<td>v.front()</td>
<td>백터의 첫번째 요소 접근</td>
</tr>
<tr>
<td>v.back()</td>
<td>백터의 마지막 요소 접근</td>
</tr>
</tbody></table>
<p>※vector의 at과 []에 대한 차이점을 설명하자면 다음과 같습니다.</p>
<p>둘다 똑같이 N번째의 요소 접근이지만 </p>
<p>at은 범위를 검사하여 범위 밖의 요소에 접근 시 예외처리를 발생시킵니다. (std::out_of_range)</p>
<p>하지만 [](operator [])는 범위검사를 하지 않으며 예외처리르 발생시키지 않습니다. 또한</p>
<p>해당범위 밖의 요소에 접근을 시도한다면 일반적인 디버깅(g++ or VC++)이 발생합니다.</p>
<p>백터는 효율을 중점으로 둔 라이브러리 함수여서 보통 []를 권장하고 있으며 여러가지 방법으로 </p>
<p>유효성 검사가 가능하기 때문에 []를 많이 사용하고 있습니다.
<br /><br /></p>
<h4 id="vector에-요소-삽입">Vector에 요소 삽입</h4>
<table>
<thead>
<tr>
<th>Method</th>
<th>기능</th>
</tr>
</thead>
<tbody><tr>
<td>v.push_back()</td>
<td>백터의 마지막 부분에 새로운 요소 추가</td>
</tr>
<tr>
<td>v.pop_back()</td>
<td>백터의 마지막 부분 제거</td>
</tr>
<tr>
<td>v.insert(삽입할 위치의 주소 값, 변수 값)</td>
<td>사용자가 원하는 위치에 요소 삽입</td>
</tr>
<tr>
<td>v.emplace(삽입할 위치의 주소 값, 변수 값)</td>
<td>사용자가 원하는 위치에 요소 삽입(move로 인해 복사생성자 X)</td>
</tr>
<tr>
<td>v.emplace_back()</td>
<td>백터의 마지막 부분에 새로운 요소 추가(move로 인해 복사생성자 X)</td>
</tr>
<tr>
<td>v.erase(삭제할 위치) or v.erase(시작위치, 끝위치)</td>
<td>사용자가 원하는 index값의 요소를 지운다.</td>
</tr>
<tr>
<td>v.clear()</td>
<td>백터의 모든 요소를 지운다.(return size = 0)</td>
</tr>
<tr>
<td>v.resize(수정 값)</td>
<td>백터의 사이즈를 조정한다.(범위 초과시 0으로 초기화)</td>
</tr>
<tr>
<td>v.swap(백터 변수)</td>
<td>백터와 백터를 스왑한다.</td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
</tbody></table>
<p>여기서 잠깐!!!! 짚고 넘어가야 할 부분이 있습니다.</p>
<p>vector에 대한 복사생성자와 move입니다.</p>
<p>기본적으로 push_back() 함수는 값을 넣는 과정에서 복사생성자를 호출하게 됩니다.</p>
<p>뿐만 아니라 insert를 하게 된다면 모든 값들을 새로운 메모리에 복사한 후 해당 자리에 값을 넣게 됩니다.</p>
<p>(일반적인 배열 중간에 값을 끼워 넣는거랑 똑같습니다.)</p>
<p>이렇게 되버리면 복사생성자로 인한 오버헤드가 커지게 되며 성능 저하를 야기합니다.</p>
<p>그래서 나온것이 emplace와 emplace_back 입니다.</p>
<p>empace와 emplace_back은 백터 내부에서 값들을 생성하는 것입니다.</p>
<p>즉, 생성자만 호출이 되죠.</p>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;vector&gt;
#include &lt;string&gt;

class A {
private:
    int num;
    std::string name;
public:
    A(int i, std::string s) : num(i), name(s) {}
};

int main(void) {
    std::vector&lt;A&gt; v;
    A a(1, &quot;hwan&quot;);

    v.push_back(1, &quot;hi&quot;);   //error -&gt; v.push_back(a);
    v.emplace_back(1, &quot;hi&quot;); //ok!!

    return 0;
}</code></pre>
<p>여기서 보면 A라는 클래스가 있습니다. 해당 클래스는 인자로 int와 string을 받지요.</p>
<p>백터 v는 해당 클래스를 담을 수 있는 배열입니다.</p>
<p>14행을 보면 v.push_back(1, &quot;hi&quot;); 를 하고 있지만 이는 삽입이 되지 않습니다.</p>
<p>push_back은 내부적으로 템플릿에 대한 생성자 호출을 지원하지 않기 때문입니다.</p>
<p>따라서 일반적으로 13행에 선언된 a 라는 변수를 넣게되며 넣을 때 복사생성자가 호출됩니다.</p>
<p>하지만 emplace_back() 같은 경우에는 v.emplace_back(1, &quot;hi&quot;);를 넣어주고 있는데 컴파일이 됩니다.</p>
<p>그 이유는 내부적으로 템플릿에 대한 생성자 호출을 해주기 때문에 편하고, 복사생성자의 호출없이</p>
<p>바로 입력이 가능해 집니다. </p>
<p>cppreference를 의 내용을 보면 둘다 move를 지원합니다.</p>
<p>하지만 내부적으로 생성자를 지원하는 함수는 emplace와 emplace_back이 유일하기 때문에</p>
<p>push_back보단 emplace_back사용을 권장해 드립니다.</p>
<p>  또한 vector의 크기에는 size()와 capacity() 두개가 있는데, </p>
<p>size()는 백터가 생성된 크기이며 capacity()는 백터의 최대 할당 크기라고 생각하시면 됩니다.</p>
<p> <img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/bc634c5f-8934-48a5-9bed-74c17cd7750b/image.png" /></p>
<p>위 사진처럼 되어 있는데 백터의 크기가 capacity()의 크기를 초과해 버린다면 reallocate(재할당)이 발생합니다.</p>
<p>재할당이 발생한다면 모든 값들을 새로운 메모리 공간에 복사한 후 기존 백터를 파괴해 버립니다.</p>
<p>여기서 복사 과정에서도 복사생성자가 발생하게 됩니다.</p>
<p>그렇게 되면 프로그램의 퍼포먼스가 저하되지요.</p>
<p>또한 reallocate이 자주 일어나는 현상을 막기 위해서 reserve()라는 함수를 사용해주면 되는데</p>
<p>이 함수는 백터의 capacity() 크기를 설정해주는 함수로 충분한 백터를 만들어서 불필요한 생성과정을 없애주는 역할을 합니다.</p>
<p>하지만 reserve()를 너무 크게 잡게되면 백터가 불필요하게 늘어나 메모리를 많이 잡아먹을 수 있습니다.</p>
<p>따라서 남은 공간을 잡아주는 함수가 바로 shrink_to_fit()이라는 함수 입니다.</p>
<p>이 함수를 통해 capacity()의 크기를 조정해 줄 수 있습니다.</p>
<p>또 한가지 clear()에 대한 설명입니다.</p>
<p>clear()로 백터의 값들을 지우게 되면 백터의 요소들은 없어지지만 capacity()는 남아있습니다.</p>
<p>즉, clear()로 백터의 값들을 지운 후 다시 사용하지 않는다면 해당 백터의 메모리 공간은 잉여로 남게 됩니다.</p>
<p>이걸 해결할 수 있는 방법이 swap을 이용한 방법인데, 사용법은 다음과 같습니다.</p>
<pre><code class="language-cpp">vector&lt;int&gt; v = { 1, 2, 3, 4};
v.clear();
cout &lt;&lt; v.capacity() &lt;&lt; endl;    //output : 10

vector&lt;int&gt;().swap(v);
cout &lt;&lt; v.capacity() &lt;&lt; endl;    //output : 0​</code></pre>
<p>이렇게 하면 아무것도 없는 백터공간과 swap이 일어나 capacity() 공간을 없앨 수 있습니다.</p>
<p>하지만 함수가 끝나면(중괄호를 벗어나면) 자동으로 힙에서 메모리 해제가 되니 한개의 함수에서</p>
<p>백터를 계속 재활용해 사용하지 않는이상 굳이 저렇게 하지 않아도 됩니다.</p>
<p>insert()와 erase()를 사용할 때도 조심해야 하는데, 해당 함수를 사용 시 변수를 찾은 후 해당 공간을 만들기 위해</p>
<p>데이터를 이동시킵니다. 하나하나 일일이요. 만약 capacity()값을 초과될 경우 reallocate도 일어나게 되므로</p>
<p>메모리 오버헤드 및 성능저하도 야기할 수 있습니다.</p>
<p>따라서 삽입과 삭제가 빈번히 일어날경우 vector보단 list나 deque를 사용하는 것이 바람직합니다.</p>
<h4 id="vector-capacity벡터-용량">Vector Capacity(벡터 용량)</h4>
<table>
<thead>
<tr>
<th>Method</th>
<th>기능</th>
</tr>
</thead>
<tbody><tr>
<td>v.empty()</td>
<td>백터가 빈공간이면 true, 값이 있다면 false</td>
</tr>
<tr>
<td>v.size()</td>
<td>백터의 크기 반환</td>
</tr>
<tr>
<td>v.capacity()</td>
<td>heap에 할당된 백터의 실제크기(최대크기) 반환</td>
</tr>
<tr>
<td>v.max_size()</td>
<td>백터가 system에서 만들어 질 수 있는 최대 크기 반환</td>
</tr>
<tr>
<td>v.reserve(숫자)</td>
<td>백터의 크기 설정</td>
</tr>
<tr>
<td>v.shrink_to_fit()</td>
<td>capacity의 크기를 백터의 실제 크기에 맞춤</td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
</tbody></table>
<pre><code class="language-cpp">  vector&lt;int&gt;v = { 1, 2, 3, 4 };

cout &lt;&lt; v.size() &lt;&lt; endl;    //output : 4
cout &lt;&lt; v.capacity() &lt;&lt; endl; //output : 10 (컴파일 환경에 따라 달라질 수 있음)

v.reserve(6);
cout &lt;&lt; v.capacity() &lt;&lt; endl; //output : 6
cout &lt;&lt; v.max_size() &lt;&lt; endl; //output : 1073741823(시스템 성능에 따라 달라질 수 있음)

v.shrink_to_fit();
cout &lt;&lt; v.capacity() &lt;&lt; endl; //output : 4

cout &lt;&lt; v.empty() &lt;&lt; endl; //output : false
v.clear();
cout &lt;&lt; v.empty() &lt;&lt; endl; //output : true​</code></pre>