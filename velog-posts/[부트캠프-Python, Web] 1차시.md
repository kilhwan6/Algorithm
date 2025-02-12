<ul>
<li><p>취업시장이 가을부턴 괜찮을 것</p>
<ul>
<li>대통령이 민주당쪽인 경우 취업이 확 뛰었음</li>
</ul>
</li>
<li><p>코딩 복습 중요</p>
<ul>
<li>복습한 사람이 다 티가 남, 잘하게 됨</li>
</ul>
</li>
</ul>
<hr />
<h2 id="1-일정-설명">1. 일정 설명</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/6c9af4c5-302d-43a6-b6ad-8de4f3bb98bc/image.png" /></p>
<h3 id="파이썬">파이썬</h3>
<ul>
<li>Anaconda 사용</li>
<li>파이썬 공부는 필요한 부분만 가져가기</li>
<li>첫 시험은 금요일, 동적 크롤링은 안 봄!</li>
</ul>
<h3 id="웹">웹</h3>
<ul>
<li><p>서버 역할이 커진 웹 프로그래밍이 많아짐</p>
</li>
<li><p>웹 기반 파이썬 AI를 만드는 수요가 많음.</p>
</li>
<li><p>웹 종류가 다양한데, Fast API를 사용</p>
<ul>
<li><p>파이썬을 많이 사용하기 때문에</p>
</li>
<li><p>Django는 좀 무거운 툴임, 공부하는 데 시간이 많이 걸림</p>
</li>
<li><p>웹에서 개발할 경우 Django까지 갈 필요도 없음</p>
</li>
<li><p>AI 모델 사용 시, 파이썬 사용도 가능하고 자바 사용도 가능함</p>
<ul>
<li>자바는 Transformer 라는 툴을 많이 사용함</li>
</ul>
</li>
<li><p>금요일에 시험 및 미니프로젝트 진행</p>
</li>
<li><p>웹은 주피터 계열로 개발이 불가, 너무 불편함</p>
<ul>
<li>VS code로 진행</li>
</ul>
</li>
</ul>
</li>
</ul>
<h3 id="sql">SQL</h3>
<ul>
<li>Heide SQL 사용</li>
</ul>
<h3 id="수업-진행-방식">수업 진행 방식</h3>
<ul>
<li>교재 위주로 진행하지는 않음<ul>
<li>수업 내용에서의 보충, 참고로 사용</li>
</ul>
</li>
</ul>
<hr />
<h2 id="2-파이썬">2. 파이썬</h2>
<h3 id="1-아나콘다-설치">1) 아나콘다 설치</h3>
<ul>
<li><p>버전을 웬만하면 맞춘다.</p>
<ul>
<li>가급적이면.
아나콘다는 연에 2번 버전업데이트를 하기 때문에</li>
<li><ol start="2024">
<li>10 발표된 아나콘다 권장</li>
</ol>
</li>
</ul>
</li>
<li><p>명령어 사용, 파이토치와 widget툴 설치</p>
<ul>
<li>conda install pytorch torchvision -c pytorch
conda install -n base -c conda-forge widgetsnbextension</li>
</ul>
</li>
<li><p>jupyter lab --notebook-dir=c:/education/pythonedu</p>
<ul>
<li>주피터랩을 해당 경로에 실행
근데 나는 다른 경로여서.. 경로 추가설정</li>
<li>lab --notebook-dir=c:/Users/user/Downloads/education/현대로템</li>
</ul>
</li>
<li><p>cmd 창에 명령어를 사용해서 실행하는 것</p>
</li>
<li><blockquote>
<p>CLI 인터페이스</p>
</blockquote>
<ul>
<li>꺽쇠 (&gt;) 가 Prompt임.</li>
<li>꺽쇠 번호 앞에 있는 것이 내가 어느 디렉토리에 있는지 알려줌</li>
<li>cd &lt;이동할 폴더 경로&gt; 혹은 &lt;현재 디렉토리에 있는 폴더&gt;<ul>
<li>디렉토리 이동</li>
</ul>
</li>
<li>이후 dir 입력하면, 명령의 경로가 이동한 곳으로 업데이트됨</li>
</ul>
</li>
<li><p>아나콘다 프롬프트는 경로 앞에 (base)가 붙어있음.</p>
<ul>
<li>(base) 는 아나콘다가 제공하는 기본 개발 환경이다!<ul>
<li>가상 개발 환경이라고도 함</li>
</ul>
</li>
</ul>
</li>
<li><p>html 연결프로그램 설정</p>
<ul>
<li>브라우저 (크롬 등) 이어야 함.
<br /> <br /><h3 id="2-주피터-노트북-기본조작">2) 주피터 노트북 기본조작</h3>
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/2ab715a5-5b04-4407-bba8-02aa7523ee32/image.png" /></li>
</ul>
</li>
<li><p>주피터 노트북에서는 파이썬 인터프리터의 역할을, 커널이 대신한다 !</p>
<ul>
<li>커널이 실행된 이후 첫 번째 실행,
실행이 되었다 안 되었다를 구분 가능</li>
</ul>
</li>
</ul>
<p><br /> <br /></p>
<h3 id="3-파이썬-소개">3) 파이썬 소개</h3>
<blockquote>
<p>귀도 반 로섬이 만든 고급 프로그래밍 언어</p>
</blockquote>
<ul>
<li>인터프리터를 사용하는 객체지향 언어, 플랫폼에 독립적인 언어</li>
<li>중괄호를 블록 단위로 사용하는 타 언어와 달리,
파이썬은 들여쓰기를 사용
<br /><br /><h3 id="4-anaconda">4) Anaconda</h3>
</li>
<li>아나콘다는 데이터 과학, 머신러닝, 데이터 분석 및 대규모 데이터 처리에 사용되는 파이썬 배포판(distribution)</li>
<li>한 번의 설치로 데이터 과학 및 분석에 필요한 주요 패키지들을 사용 가능
<br /> <br /><h3 id="5-jupyterlab">5) JupyterLab</h3>
</li>
<li>Jupyter Lab은 데이터 과학 및 분석 그리고 AI 프로그래밍에서 많이 선택되고 있는 Jupyter Notebook 의 업그레이드 버전 에디터 툴이다.</li>
<li>파이썬 인터프리터를 대화형 모드로 사용할 수 있기 때문에 파이선 코드를 입력하면 코드의 실행 결과를 바로 확인할 수 있다.</li>
<li>실행 단위는 Cell(코드박스)로서 코드들을 작성한 후 shift+Enter 입력 시 실행 결과를 바로 아래 출력 공간에서 볼 수 있다. </li>
<li>유사한 프로그램으로 Google의 Colab이 있다.</li>
</ul>
<hr />
<h2 id="3-파이썬-문법">3. 파이썬 문법</h2>
<h3 id="1-데이터타입리터럴-변수">1. 데이터타입(리터럴, 변수)</h3>
<ul>
<li>리터럴 : 데이터값<ul>
<li>100</li>
<li>0x100</li>
<li>True</li>
<li>False</li>
<li>None</li>
<li>&quot;KIM&quot;, &quot;가나다&quot;, &quot;100&quot;</li>
<li><strong>리터럴의 경우 데이터 타입을 잘 맞춰 줘야 함</strong></li>
<li>Primitive<ul>
<li>int, float, str, bool. complex<ul>
<li>int
28바이트, 무지 큼 범위가</li>
</ul>
</li>
</ul>
</li>
<li>Data<ul>
<li>list, tuple, set, dict</li>
</ul>
</li>
</ul>
</li>
</ul>
<ul>
<li>변수 : 메모리의 일정 공간에 만든 방<ul>
<li>이름을 붙임</li>
<li>&quot;=&quot; 연산자 사용</li>
<li>변수명 = 값<ul>
<li>값의 자리에는 리터럴, 변수, 연산식, 함수호출식 전부 올 수 있다.</li>
</ul>
</li>
<li>v1 = 10</li>
<li>l-v, r-v</li>
</ul>
</li>
</ul>
<h3 id="2-제어문">2. 제어문</h3>
<ul>
<li>조건제어문<ul>
<li>if</li>
<li>match</li>
</ul>
</li>
<li>반복제어문<ul>
<li>for</li>
<li>while</li>
</ul>
</li>
<li>분기 제어문<ul>
<li>break</li>
<li>continue</li>
</ul>
</li>
<li>연산자</li>
<li>함수</li>
<li>OOP</li>
<li>예외처리</li>
</ul>
<h3 id="3-수업">3. 수업</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/889d51ec-4f77-42d2-a6aa-bebc9eb5863d/image.png" /></p>
<ul>
<li>바이트 bytes : 0~255 사이의 코드 모임 <ul>
<li>b&quot;Python&quot;</li>
</ul>
</li>
<li>int<ul>
<li>이진수0b010 </li>
<li>8진수 0o642</li>
<li>16진수 0xF3</li>
<li>코드를 많이 보며 익숙해져야함
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/59caf9be-e073-4f22-8b8e-2f8746aa3820/image.png" /></li>
</ul>
</li>
<li>문자열 str<ul>
<li>앞뒤로 인용본이 길게 나오면, &quot;&quot;&quot; 사용</li>
</ul>
</li>
<li>bytes : 앞뒤로 \ 사용</li>
</ul>
<h3 id="4-함수">4. 함수</h3>
<ul>
<li><p>어떤 일을 수행하는 명령을 하나로 묶어 이름 부여</p>
</li>
<li><p>반복적으로 사용하는 기능을 함수로 생성하면 편리함</p>
</li>
<li><p>어떤 기능 필요할 때마다 호출</p>
</li>
<li><p>어떻게 만들었는지에 따라 다르게 호출하게 됨</p>
</li>
<li><p>print()</p>
<ul>
<li>파이썬 내장 함수, 출력 함수</li>
<li>print(type(100))<ul>
<li>&lt;class 'int'&gt;
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/1289bd34-0a59-462b-b83b-f63adc8c0871/image.png" /></li>
</ul>
</li>
</ul>
</li>
<li><p>api, library</p>
<ul>
<li>자주 쓰는 함수를 미리 만들어둔 것, 기능을 모아둔 것</li>
</ul>
</li>
<li><p>내장 함수</p>
<ul>
<li>파이썬 언어에서 제공하는 함수</li>
</ul>
</li>
</ul>
<h3 id="5-식별자">5. 식별자</h3>
<ul>
<li>변수명, 함수명 등 명칭 정할때 사용</li>
<li>규칙이 있음<ul>
<li>예약어 사용 불가 </li>
<li>특문은 언더바_만 허용</li>
<li>숫자로 시작하면 안 됨</li>
<li>공백을 포함할 수 없음</li>
<li>가급적 알파벳 사용</li>
<li>유의미한 의미로 짓되, 직관성이 있어야 함</li>
</ul>
</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/43ccea96-42fd-4d89-8b89-0017df9afad8/image.png" /></p>
<h3 id="6-연산자">6. 연산자</h3>
<ul>
<li>산술 연산자<ul>
<li>가감승제</li>
<li>최우선 순위</li>
</ul>
</li>
<li>관계 연산자<ul>
<li>대소 구별</li>
<li>두번째 순위</li>
</ul>
</li>
<li>논리 연산자<ul>
<li>참, 거짓</li>
<li>세번째 순위</li>
</ul>
</li>
<li>대입 연산자<ul>
<li>최후순위</li>
</ul>
</li>
</ul>
<h3 id="7-기타">7. 기타</h3>
<ul>
<li><p>print() 문 사용 시, 특이한 현상</p>
<pre><code class="language-python">v1 = &quot;ABC&quot;
v2 = &quot;가나다&quot;
print(v1)
print(v1, v2)
print(v1, v2, sep=&quot;&quot;)
print(v1, v2, sep=&quot;@&quot;)</code></pre>
</li>
<li><p>결과</p>
<pre><code class="language-python">ABC
ABC 가나다
ABC가나다
ABC@가나다</code></pre>
</li>
<li><p>print() 함수는 기능을 살펴보면 심지어
파일로도 출력이 가능함.</p>
<ul>
<li>그러나 사용하는 개발자는 별로 없음.
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/1c46be03-dc16-4cc2-b6a6-d7daf827b0db/image.png" /></li>
</ul>
</li>
<li><p>print에서 합쳐진 문자열을 출력할 때, 
숫자는 str()로 형변환해서 문자열로 만든 뒤 출력해야 함.</p>
</li>
<li><p>input() 함수에서는 str형태로 받음.</p>
<ul>
<li>만약 int형으로 내가 출력하거나, 계산하고 싶다면
int()함수를 사용해 형변환함</li>
</ul>
</li>
<li><p>함수명, 변수명, 클래스명 정할때 공통사항</p>
<ul>
<li>파이썬 : 스네이크 표기법(케밥 표기법)<ul>
<li>draw_string()</li>
<li>find_by_id()</li>
<li>언더바를 마니 사용</li>
</ul>
</li>
<li>자바(자바스크립트) : 카멜케이스 표기법(낙타 표기법)<ul>
<li>drawString()</li>
<li>findByid()</li>
<li>새로운 단어 등장할 때, 첫 번째는 대문자를 사용</li>
</ul>
</li>
</ul>
</li>
<li><p>여러 행으로 개행되는 문자열 적을 때, 시작 및 끝에 &quot;&quot;&quot; 붙여 str생성</p>
</li>
<li><p>print문에서 출력할 때, 숫자를  f-string으로 출력</p>
<pre><code class="language-python">print('x = ', x, ', y = ', y, sep=&quot;&quot;)
print(f'x = {x}, y = {y}')  # f-string</code></pre>
<ul>
<li>결과는 동일</li>
</ul>
</li>
</ul>
<h2 id="3-파이썬의-제어문">3. 파이썬의 제어문</h2>
<h3 id="1-조건문">1. 조건문</h3>
<ul>
<li><p>if</p>
<ul>
<li>조건에 따른 내용 실행</li>
<li>if, else문에서 같은 조건루프에 속한 문장은,
들여쓰기를 잘 수행해야 한다.</li>
<li>특이하게  if, else 이후 : 을 사용해 조건 이후 실행문과 구분</li>
<li><h3 id="2-반복문">2. 반복문</h3>
</li>
</ul>
</li>
<li><p>for</p>
</li>
<li><p>while</p>
</li>
</ul>
<hr />
<h2 id="기타">기타</h2>