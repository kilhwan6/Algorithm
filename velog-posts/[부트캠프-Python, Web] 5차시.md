<h1 id="문자열-포매팅">문자열 포매팅</h1>
<hr />
<h2 id="1-문자열-포매팅formatting">1. 문자열 포매팅(formatting)</h2>
<h3 id="1-포맷">1) 포맷</h3>
<ul>
<li>문자열 결합 : 문자열 결합 + 연산자 사용</li>
<li>% 포매팅 : %문자를 사용해서 원하는 형식으로 포맷팅하는 방법<ul>
<li>(% + 자료형 종류) 형식으로 사용</li>
</ul>
</li>
<li>format() 내장 함수</li>
<li>문자열의 format() 메서드</li>
<li>f문자열(f-string)</li>
</ul>
<h3 id="2-포맷-문자열-사용">2) 포맷 문자열 사용</h3>
<ul>
<li>포맷 문자열로 자릿수 표현<pre><code class="language-python">fs =  &quot;4.3f&quot;
value = 100.66666
print(format(value, fs))
</code></pre>
</li>
</ul>
<p>결과
100.667</p>
<pre><code>
- 포맷 문자열로 여러 포맷들을 표현
```python
fstr = &quot;{:f}, {:d}, {:s}, {:o}, {:x}&quot;
print(fstr.format(100.6666666, 100, &quot;가나다&quot;, 100, 100))

결과
100.666667, 100, 가나다, 144, 64</code></pre><ul>
<li>포맷 문자열 표현 방식 4가지<pre><code class="language-python">name = &quot;둘리&quot;
age = 16
height = 162.5
print(&quot;이름:%s, 나이:%d, 키:%.1f&quot; % (name, age, height))
</code></pre>
</li>
</ul>
<p>name = &quot;둘리&quot;
age = 16
height = 162.5
print(&quot;이름:&quot;+format(name, &quot;s&quot;), &quot;나이:&quot;+format(age, &quot;d&quot;), &quot;키:&quot;+format(height, &quot;.1f&quot;), sep=&quot;, &quot;)</p>
<p>name = &quot;둘리&quot;
age = 16
height = 162.5
print(&quot;이름:{:s}, 나이:{:d}, 키:{:.1f}&quot;.format(name, age, height))</p>
<p>name = &quot;둘리&quot;
age = 16
height = 162.5
print(&quot;이름:{}, 나이:{}, 키:{}&quot;.format(name, age, height))</p>
<p>결과
이름:둘리, 나이:16, 키:162.5</p>
<pre><code>
- 포맷 문자열의 정렬
  - 문자열은 왼쪽 정렬
  - 숫자는 오른쪽 정렬

- 문자열 정렬 변경 시, ^, &gt;, &lt;을 포맷 앞에 붙여 사용해 정렬 변환

- 출력 문자열보다 포맷이 클 때, 공백을 다른 문자로 채울 수 있음

- 형식

```python
name = &quot;둘리&quot;
age = 16
height = 162.5
print(f&quot;이름:{name:_^10s}, 나이:{age:_&gt;5d}, 키:{height:_&lt;8.2f}&quot;)

결과
이름:____둘리____, 나이:___16, 키:162.50__</code></pre><br />

<hr />
<h1 id="실습-7-문제풀이">실습 7 문제풀이</h1>
<h3 id="문제-1">문제 1</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/92106003-fc18-4ef8-92b1-052f40fb5636/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 1번
</code></pre>
</li>
</ul>
<p>dic_score = {&quot;둘리&quot; : 90, &quot;또치&quot; : 95, &quot;도우너&quot; : 80, &quot;고길동&quot; : 70, &quot;마이콜&quot; : 75, &quot;희동이&quot; : 80}</p>
<p>stud_num = len(dic_score)
score_dul = dic_score[&quot;둘리&quot;]</p>
<p>print(f&quot;전체 학생은 {stud_num}명이고 둘리의 점수는 {score_dul}점입니다.&quot;)</p>
<pre><code>
### 문제 2
![](https://velog.velcdn.com/images/yookkilhwan/post/b85301dd-f24d-4361-953c-dfbd403b0520/image.png)

- 풀이
```python
# 2번

dic_color_rgb = {&quot;red&quot; : &quot;#ff0000&quot;, &quot;blue&quot; : &quot;#0000ff&quot;, &quot;green&quot; : &quot;#008000&quot;, &quot;yellow&quot; : &quot;#ffff00&quot;, &quot;orange&quot; : &quot;#ffa500&quot;,  &quot;black&quot; : &quot;#000000&quot;, &quot;white&quot; : &quot;#ffffff&quot;, &quot;violet&quot; : &quot;#ee82ee&quot;, &quot;pink&quot; : &quot;#ffc0cb&quot;, &quot;lime&quot; : &quot;#00ff00&quot;}
keys_list = list(dic_color_rgb.keys())

print(f&quot;주어진 color는 {keys_list}입니다.&quot;)
color = input(&quot;칼라명을 영문으로 입력하세요. : &quot;)

if color in dic_color_rgb:
    print(f&quot;{color}칼라의 RGB값은 {dic_color_rgb.get(color)}입니다.&quot;)
else :
    print(f&quot;{color}칼라의 RGB값을 찾을 수 없습니다.&quot;)</code></pre><h3 id="문제-3">문제 3</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/c05d63b7-4600-4ed1-a2e4-7eb6c25dae86/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 3번
</code></pre>
</li>
</ul>
<p>dic_day_temp = {&quot;월&quot; : (3, -7), &quot;화&quot; : (2, -8), &quot;수&quot; : (2, -8), &quot;목&quot; : (3, -8), &quot;금&quot; : (3, -8),  &quot;토&quot; : (2, -8),  &quot;일&quot; : (2, -7)}</p>
<p>print(&quot;요일명 입력 예시는 다음과 같습니다 : 월&quot;)
day = input(&quot;요일명을 한글로 입력하세요 : &quot;)</p>
<p>if day in dic_day_temp:
    print(f&quot;{day}요일의 최저온도는 {dic_day_temp.get(day)[1]}이고 최고 온도는 {dic_day_temp.get(day)[0]}입니다.&quot;)
else :
    print(f&quot;{day}요일의 정보를 찾을 수 없습니다.&quot;)</p>
<pre><code>### 문제 4
![](https://velog.velcdn.com/images/yookkilhwan/post/befc9451-accb-49ed-bd56-8de64ae09f1e/image.png)

- 풀이
```python
# 4번

import random

set1 = set()
set2 = set()

for i in range(0, 20):
    set1.add(random.randint(1,20))
    set2.add(random.randint(1,20))

print(f&quot;집합 1 : {set1}&quot;)
print(f&quot;집합 2 : {set2}&quot;)
print(f&quot;두 집합에 모두 있는 데이터 : {set1&amp;set2}&quot;)
print(f&quot;집합1 또는 집합2에 있는 데이터 : {set1|set2}&quot;)
print(f&quot;집합1에는 있고 집합2에는 없는 데이터 : {set1-set2}&quot;)
print(f&quot;집합2에는 있고 집합1에는 없는 데이터 : {set2-set1}&quot;)
print(f&quot;집합1과 집합2가 각자 가지고 있는 데이터 : {set1 ^ set2}&quot;)</code></pre><ul>
<li>여러 개의 난수 생성할 때, random 라이브러리의 sample 메서드로 대체 가능</li>
</ul>
<h3 id="문제-5">문제 5</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/df41bcb5-4ecf-4738-9056-f771540f9672/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 5번
</code></pre>
</li>
</ul>
<p>import random</p>
<p>set1 = set()</p>
<p>count = 0;
while(1) : 
    set1.add(random.randint(1,45))
    count += 1
    if len(set1) == 6 :
        break</p>
<p>print(f&quot;행운의 로또번호 : {set1}\n 반복 횟수 : {count}회&quot;)</p>
<pre><code>- 중복에 유의해 for이 아닌 while을 사용해야 함.

---
## 2. 패킹과 언패킹

&gt;나열된 자료들을 특정 형식으로 묶고, 푸는 일

### 패킹
- 나열해 대입하면, 알아서 괄호가 없는 튜플로 해석
```python
a, *b, c = 10, 20, 30, 40 # 나열된 값을 튜플로 패킹한 후에 언패킹하여 각각의 변수에 대입함
print(&quot;# 괄호가 없는 튜플을 활용한 할당&quot;)
print(&quot;a:&quot;, a)
print(&quot;b:&quot;, b)
print(&quot;c:&quot;, c)

결과
# 괄호가 없는 튜플을 활용한 할당
a: 10
b: [20, 30]
c: 40</code></pre><ul>
<li><p>설명</p>
<ul>
<li>*b는 시작, 끝 값 제외한 중간 값들</li>
<li>리스트로 나머지 값을 다 집어넣어준다</li>
</ul>
</li>
<li><p>세트와 딕셔너리 형태도 패킹, 언패킹 가능</p>
</li>
</ul>
<h3 id="언패킹">언패킹</h3>
<ul>
<li>출력 시 형식에 맞춰 알아서 출력해줌</li>
</ul>
<hr />
<h2 id="3-시퀀스-자료형">3. 시퀀스 자료형</h2>
<blockquote>
<p>반복이 가능한 객체 중, 시퀀스 객체는
리스트, 튜플, range, 문자열</p>
</blockquote>
<p>반복해서 문자를 꺼내고 넣을 수 있음</p>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/b97ba5bf-f5f1-468f-b116-d3a67cef9cf6/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/755eed81-bd17-46a6-aa78-95409f0918ce/image.png" /></p>
<h3 id="문자열-리스트">문자열, 리스트</h3>
<ul>
<li>내용, 구조 변경 가능</li>
</ul>
<h3 id="튜플">튜플</h3>
<ul>
<li>내부 내용, 구조 변경 불가</li>
</ul>
<h3 id="iterable-성질">iterable 성질</h3>
<ul>
<li>한 번에 하나의 데이터를 반환할 수 있는 성질</li>
<li>iter() 함수로 iterator객체를 생성할 수 있음</li>
<li>확인 방법<pre><code class="language-python">obj = range(10)
# obj = {&quot;name&quot; : &quot;둘리&quot;}
type(obj)
</code></pre>
</li>
</ul>
<p>range</p>
<p>hasattr(obj, &quot;<strong>iter</strong>&quot;)</p>
<p>True</p>
<p>from typing import Iterable
isinstance(obj, Iterable)</p>
<p>True</p>
<p>iterator = iter(obj)
print(iterator)</p>
<p>&lt;range_iterator object at 0x00000147D47D5A10&gt;</p>
<pre><code>
---

## 4. 모듈
&gt; 다른곳에서 사용 가능하도록 완성된 파이썬 소스

### 모듈

- .py로 끝나는 파이썬 소스
- 함수, 클래스, 변수 등 포함
- 다른곳에서 import해서 사용 가능
- 파이썬 인터프리터가 직접 실행시키는 파이썬 소스에 자동으로 부여되는 모듈명 : __main__
![](https://velog.velcdn.com/images/yookkilhwan/post/e8b0e5b7-a840-4026-a16e-6b01c86e2c92/image.png)

### 패키지
- 모듈을 모아놓은 폴더
- 종종 라이브러리라고 부름
  - 라이브러리는 패키지의 집합, 그러나 혼용해서 사용
  - ex) 넘파이 라이브러리, 넘파이 패키지
- 패키지가 커지면, 안에 서브패키지가 생길 수도 있음
- 모듈을 같은 속성끼리 모아놓기 위해 사용

![](https://velog.velcdn.com/images/yookkilhwan/post/407ff958-da89-47ac-aff8-a31947554df3/image.png)

### 파이썬 내장 함수, 패키지

- PyPI
  - 파이썬 패키지 리포지토리
  - 파이썬을 위한 오픈소스 패키지 저장소
- pip
  - 파이썬으로 작성된 패키지 소프트웨어를 설치, 관리하는 패키지 관리 시스템

- os 모듈
  - 파이썬에서 관리하는 운영체제 관련 라이브러리
  - 어떤 함수를 관리하는지 보고 싶으면
  - os 모듈에서 dir 입력

  ![](https://velog.velcdn.com/images/yookkilhwan/post/ecf89ca6-1db0-4f19-834a-fdc694fd4cba/image.png)

- 파이썬의 내장 함수
![](https://velog.velcdn.com/images/yookkilhwan/post/4a9c1233-3d6b-4f6e-a5ff-1a2d1877ec80/image.png)

---


## 6. 함수
&gt; input을 받아서 정해진 기능을 수행하고 output을 반환하도록, 잘 조직화되고 재사용이 가능한 코드 블록

### 사용자 정의 함수
- User-Defined Function, UDF)
- 유용한 이유
  - 재사용 가능
  - 코드를 구조화, 모듈화함으로써 관리하기 쉽다
  - 분산해서 개별적으로 작성 가능
  -&gt; **애플리케이션 개발 속도 상승**

- 아규먼트 : 함수를 호출할 때 **전달하는 데이터 값**
- 매개변수 : 아규먼트를 **전달받는 함수**

### 함수의 return
- 함수에서 반환문이 없을 경우, print 시 None을 반환

```python
def test():
    print(&quot;UNICO&quot;)

print(test())</code></pre><pre><code class="language-css">UNICO
None</code></pre>
<ul>
<li>이유 분석</li>
</ul>
<ol>
<li>test() 함수가 정의되어 있으며, 내부에서 &quot;UNICO&quot;를 출력하는 print() 문이 실행됩니다.</li>
<li>print(test())를 실행하면, 함수를 호출하면서 test() 내부의 print(&quot;UNICO&quot;)가 먼저 실행되어 &quot;UNICO&quot;가 출력됩니다.</li>
<li>test() 함수에는 return 문이 없기 때문에 자동으로 None을 반환합니다.</li>
<li>print(test())는 결국 print(None)을 실행하는 것과 같아서 &quot;None&quot;이 출력됩니다.</li>
</ol>
<h3 id="함수에서의-패킹-언패킹">함수에서의 패킹, 언패킹</h3>
<ul>
<li>튜플로 묶어서 패킹해 리턴</li>
</ul>
<pre><code class="language-python">def myfunc1():
    return 1,10,100  # 튜플로 패킹하여 리턴함
result = myfunc1()
print(result)
print(type(result))</code></pre>
<ul>
<li><p>결과</p>
<pre><code class="language-css">(1, 10, 100)
&lt;class 'tuple'&gt;</code></pre>
</li>
<li><p>함수의 아규먼트는 앞에 *를 붙여야 언패킹을 처리하게 됨</p>
</li>
</ul>
<pre><code class="language-python">def myfunc4(p1, p2, p3):
    return p1+p2+p3
print(myfunc4(100,200,300))
nums = [10, 20, 30]
print(myfunc4(*nums)) # 함수의 아규먼트는 앞에 * 을 붙여주어야  언패킹을 처리하게 됨</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/3915eb22-cca1-478c-97d8-36a2c8f2f481/image.png" /></p>
<ul>
<li>키워드 인수, 위치 인수의 혼용 시
키워드 인수를 사용하면 그 뒤에 위치 인수를 넣을 수 없다!</li>
</ul>
<pre><code class="language-python">def normalfn(p1, p2, p3) :
    print(p1)
    print(p2)
    print(p3)

normalfn(p1=10, 20, 30)  # 오류 발생 ❌
normalfn(10, 20, p3=30)  # 정상 실행 ⭕</code></pre>
<ul>
<li>결론 및 정리</li>
</ul>
<ol>
<li>키워드 인수를 사용하면, 그 뒤에 위치 인수를 넣을 수 없다.<pre><code class="language-python">normalfn(p1=10, 20, 30)  # ❌ 오류 발생
normalfn(10, 20, p3=30)  # ✅ 정상 실행</code></pre>
</li>
<li>위치 인수 먼저, 키워드 인수 나중이면 OK<pre><code class="language-python">normalfn(10, 20, p3=30)  # ✅ 정상 실행</code></pre>
</li>
<li>모든 인수를 키워드 방식으로 전달하면 OK<pre><code class="language-python">normalfn(p1=10, p2=20, p3=30)  # ✅ 정상 실행</code></pre>
</li>
</ol>
<h3 id="기본값디폴트-매개변수">기본값(디폴트) 매개변수</h3>
<ul>
<li>변수에 기본값이 이미 입력되어, 키워드 인수를 넣던, 위치 인수를 넣던 호환이 됨.</li>
<li>인수 개수를 적게 넣었을 경우, 키워드 인수를 잘못 쓴 것만 아니라면 기본값으로 함수가 실행됨</li>
</ul>
<h3 id="가변-매개변수">가변 매개변수</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/308b7bb4-125c-4b7d-82c1-6ca5bb9ee5ef/image.png" /></p>
<ul>
<li>값만 나열되는 형식으로 받겠다.</li>
<li><em>는 튜플 형식으로 받고, *</em>는 딕셔너리 형식으로 받는다.<pre><code class="language-python"># 가변형 인자 함수 정의
def sum_all(*p) :
  &quot;&quot;&quot;가변 위치 아규먼트로 전달되는 모든 숫자들의 합을 리턴&quot;&quot;&quot; # docstring
  print(&quot;p의 타입 :&quot;, type(p))
  sum = 0
  for data in p :
      sum += data
  return sum</code></pre>
</li>
</ul>