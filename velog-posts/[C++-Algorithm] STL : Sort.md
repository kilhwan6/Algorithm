<h3 id="1-swea_1208--flatten-문제-풀던-중">1. SWEA_1208 : Flatten 문제 풀던 중</h3>
<p>입력받은 map을 정렬하지 않고 그냥 풀려고 했는데
연산이 굉장히 복잡해지는 것을 경험함..</p>
<p>그 결과로 STL  의 Sort 메소드 사용을 고려하기 전에
스터디한 내용을 적어 보는 글입니다.
<br /><br /></p>
<h3 id="2-사용법">2. 사용법</h3>
<p>  sort()함수는 기본적으로 오름차순 정렬을 수행하는데, 
  배열의 시작점 주소와 마지막 주소 +1을 적어주면 됨.</p>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;algorithm&gt;
using namespace std;
int main(void) {
    int a[10] = { 9, 3, 5, 4, 1, 10, 8, 6, 7, 2 };
    sort(a, a + 10);
    for (int i = 0; i &lt; 10; i++) {
        cout &lt;&lt; a[i] &lt;&lt; &quot; &quot;;
    }
}</code></pre>
<p>만약 배열의 시작부터 끝까지 적지 않았다면? 
  예를 들어서 시작점 + 2부터 마지막 주소 +1까지 적었다면?
  그러면 해당 주소들 제외하고는 정렬되지 않는다.
   <br /><br />                     </p>
<h3 id="3-sort함수의-숨겨진-부분">3. sort()함수의 숨겨진 부분</h3>
<p>정렬 기준을 원하는 형태로 설정할 수 있다는 점</p>
<p>compare()함수를 다음과 같이 반환값을 큰(Greater)으로 바꿔주면 내림차순 정렬로 변환됨. 크다는 것의 기준은 '왼쪽이 오른쪽에 비해서'를 기준으로 삼음</p>
<p>데이터 비교 시, 실무에서 내무적으로 여러 변수를 정렬하는 방법을 적용한 예시</p>
<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;algorithm&gt;

using namespace std;

class Student {
public:
    string name;
    int score;
    Student(string name, int score) {
        this-&gt;name = name;
        this-&gt;score = score;
    }
    //정렬 기준은 '점수가 작은 순서'
    bool operator &lt;(Student &amp;student) {
        return this-&gt;score &lt; student.score;
    }
 };

bool compare(int a, int b) {
    return a &gt; b;
}

int main(void) {
    Student students[] = {
        Student(&quot;나동빈&quot;, 90),
        Student(&quot;나동빈&quot;, 90),
        Student(&quot;나동빈&quot;, 90),
        Student(&quot;나동빈&quot;, 90),
        Student(&quot;나동빈&quot;, 90)
    };
    sort(students, students + 5);
    for (int i = 0; i &lt; 5; i++) {
        cout &lt;&lt; students[i].name &lt;&lt; ' ';
    }
}
</code></pre>