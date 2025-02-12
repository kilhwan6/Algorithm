<h1 id="제어문">제어문</h1>
<blockquote>
<p>반복이나 조건으로 문장을 제어하는 구문</p>
</blockquote>
<br />

<hr />
<h2 id="1-조건문--if-문">1. 조건문 : if 문</h2>
<blockquote>
<p>특정 조건에서만 동작이 이루어지도록 사용</p>
</blockquote>
<br />

<h3 id="if-문-특징">if 문 특징</h3>
<ul>
<li>중첩 상관없이 구성 가능</li>
<li>안에 조건문 구성 가능</li>
</ul>
<pre><code class="language-python">import random
grade = random.randint(1,6)
if grade &gt;= 1 and grade &lt;= 3:
    print(f&quot;{grade} 학년은 저학년입니다.&quot;)
elif grade &gt;= 4 and grade &lt;= 6:
    print(f&quot;{grade} 학년은 고학년입니다.&quot;)
else :
    print(f&quot;range error - grade :{grade}&quot;)</code></pre>
<br />

<h3 id="-연산자">:= 연산자</h3>
<ul>
<li>🔍 파이썬의 := 대입 연산자 (월러스 연산자, Walrus Operator)<ul>
<li>📌 := 연산자는 &quot;할당 표현식 (Assignment Expression)&quot; 이라고 불리며,
변수를 선언하면서 동시에 값을 할당하는 연산자입니다.
파이썬 3.8 버전부터 도입되었습니다.</li>
</ul>
</li>
<li>:= 연산자의 장점<ul>
<li>1️⃣ 중복 계산을 줄여 코드 최적화<pre><code class="language-python">name = &quot;Python&quot;
if len(name) &gt; 3:
print(name+&quot;의 길이는 &quot;+str(len(name)) +&quot;이다&quot;)  # len(name) 중복 계산</code></pre>
</li>
</ul>
</li>
</ul>
<pre><code class="language-python">name = &quot;Python&quot;
if (n := len(name)) &gt; 3:
    print(name+&quot;의 길이는 &quot;+str(n) +&quot;이다&quot;)  # len(name) 1번만 계산!</code></pre>
<blockquote>
<p>✔ 변수를 선언하면서 바로 조건문에 활용할 수 있어 중복 계산을 줄이고 코드가 간결해짐!</p>
</blockquote>
<ul>
<li>:=는 if, while, 리스트 컴프리헨션 등 표현식 안에서만 사용 가능</li>
<li>파이썬 3.8 이상에서 지원됨</li>
</ul>
<br />

<h3 id="match-case-문">match-case 문</h3>
<ul>
<li>파이썬 3.10 이상에서 도입</li>
<li>기존 if-else문보다 더 깔끔하고 가독성이 좋음</li>
<li>언더바(와일드카드)로 else의 경우를 처리</li>
<li>예시</li>
</ul>
<pre><code class="language-python">grade = input('학년을 입력하세요&gt; ')  # 사용자로부터 학년을 입력받음

match grade:
    case '1' | '2' | '3' :  # grade가 '1', '2', '3' 중 하나인 경우
        print(grade + '학년은 저학년입니다.')
    case '4' | '5' | '6' :  # grade가 '4', '5', '6' 중 하나인 경우
        print(f'{grade}학년은 고학년입니다.')    
    case _ :  # 위 조건에 해당하지 않는 경우 (와일드카드 `_` 사용)
        print('1 ~ 6 까지만 입력 가능!')</code></pre>
<ul>
<li>설명
✅ match-case 문 설명
match grade:
→ grade의 값에 따라 여러 case 중 하나를 실행
case '1' | '2' | '3':
→ grade가 '1', '2', '3' 중 하나라면 해당 블록 실행
case '4' | '5' | '6':
→ grade가 '4', '5', '6' 중 하나라면 해당 블록 실행
case _:
→ 와일드카드 _ 는 위 모든 case에 해당하지 않는 경우를 처리</li>
</ul>
<br />

<hr />
<h2 id="2-반복문--for문">2. 반복문 : for문</h2>
<blockquote>
<p>정해 놓은 횟수를 반복할 때, 혹은 정해 놓은 횟수만큼 전달받아서 반복할 때 사용</p>
</blockquote>
<br />

<h3 id="for-문-특징">for 문 특징</h3>
<ul>
<li>횟수를 정해서 무언가 반복해야 할 때, 효율적인 실행</li>
<li>어떤 숫자를 계속해서 감소시키거나,
함수를 일정 횟수 실행하는 경우.
혹은 어떤 객체를 반복해서 생성하는 경우<br />

</li>
</ul>
<h3 id="range함수를-통한-처리">range함수를 통한 처리</h3>
<ul>
<li><p>range(시작, 종료, 간격)</p>
<ul>
<li>시작점부터 (종료점-1)까지 반복</li>
</ul>
</li>
<li><p>원소 개수에 따라 다르다</p>
<ul>
<li>range(2)<ul>
<li>0부터 시작, 1까지 반복</li>
</ul>
</li>
<li>range(1, 6)<ul>
<li>1부터 시작, 5까지 반복</li>
</ul>
</li>
<li>range(1, 6, 2)<ul>
<li>1부터 시작, 1, 3, 5 반복</li>
</ul>
</li>
</ul>
</li>
<li><p>실행 예시
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/83f12720-8dcf-461d-a507-b2a3d740c4a2/image.png" /></p>
</li>
</ul>
<br />

<h3 id="break문">break문</h3>
<ul>
<li>반복문이 더 이어지지 않고, 루프를 벗어나도록 함</li>
<li>예시<pre><code class="language-python">for v in range(1, 6) :
  print(v)
  if v == 3 :
      break
else :
  print(&quot;1~5 출력 완료&quot;)</code></pre>
</li>
<li>결과 </li>
</ul>
<pre><code class="language-python">1
2
3</code></pre>
<br />

<h3 id="continue문">continue문</h3>
<ul>
<li>반복문 중간에 넣으면, 이후 작업을 수행하지 않고
다음 루프로 이동하도록 함</li>
</ul>
<br />

<hr />
<h2 id="3-반복문--while문">3. 반복문 : While문</h2>
<blockquote>
<p>어떤 조건이 참이 아닐 때까지, 무한히 반복</p>
</blockquote>
<br />

<h3 id=""></h3>
<hr />
<h2 id="기타사항">기타사항</h2>
<ul>
<li><p>random 함수</p>
<pre><code class="language-python">import random
num = random.randint(1, 20)</code></pre>
<ul>
<li><p>설명
1부터 20중 수를 랜덤하게 할당</p>
</li>
<li><p>end 변수 역할</p>
<ul>
<li>개행문자로, 보통 \n으로 표시, 줄바꿈이 기본</li>
</ul>
</li>
</ul>
<pre><code class="language-python">print(num, end=&quot;&quot;)</code></pre>
<ul>
<li>다음과 같은 형태로 줄바꿈 이외의 개행형식으로 변경 가능</li>
<li>개행문자 \t는 탭 정도로 띄워줌.</li>
</ul>
</li>
</ul>