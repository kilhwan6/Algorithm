<h1 id="제어문">제어문</h1>
<br />

<hr />
<h2 id="1-while-문">1. While 문</h2>
<h3 id="문제-1">문제 1</h3>
<ul>
<li>5부터 10사이의 난수를 추출한다.</li>
<li>while 문을 사용해서 1부터 추출된 숫자값까지의 각 숫자들의 값과 제곱값을 행단위로 출력한다.</li>
<li>만일 7이 추출된다면  <pre><code>  1 - 1
   2 - 4
   3 - 9
   4 - 16
   5 - 25
   6 - 36
   7 - 49</code></pre><br /></li>
<li>풀이<pre><code class="language-python"># 1번
import random
</code></pre>
</li>
</ul>
<p>#난수 할당
randnum = random.randint(5, 10)
#print(randnum) #난수 확인용</p>
<p>#반복을 위한 count 할당
count = 0</p>
<p>while( count &lt;= randnum):#count가 randnum과 같거나 작을 경우 반복</p>
<pre><code>print(f&quot;{count} - {count**2}&quot;)#원하는 변수 출력
count += 1 #연산 이후 count 1 증가, randnum까지</code></pre><pre><code>&lt;br&gt;

### 문제 2
- &lt;span style=&quot;color:red;font-weight:bold&quot;&gt;1부터 6사이의 두 개 난수를 추출하여 각각 pair_num1, pair_num2 에 저장한다.&lt;/span&gt;
- while 문으로 다음 기능을 반복하도록 한다.
  반복 기능 : 추출된 두 개의 숫자의 값이 다른지 비교하고 서로 다르면
             &quot;pair_num1(X) 변수의 값이 pair_num2(Y) 변수의 값보다 크다.&quot;
              또는
             &quot;pair_num1(X) 변수의 값이 pair_num2(Y) 변수의 값보다 작다.&quot; 
              를 출력한다.
             &lt;span style=&quot;color:red;font-weight:bold&quot;&gt;1부터 6사이의 두 개 난수를 추출하여 각각 pair_num1, pair_num2 에 저장한다.&lt;/span&gt;

- 추출된 두 개의 숫자가 동일하면 &quot;게임 끝&quot;이라는 메시지를 출력하고 종료한다.
- &lt;span style=&quot;color:red;font-weight:bold&quot;&gt;무한 루프를 사용하지 않고&lt;/span&gt; 구현한다.
&lt;br&gt;
- 풀이
```python
# 2번
import random

#난수 초기화
# 2번
import random

#난수 초기화
pair_num1 = random.randint(1, 6)
pair_num2 = random.randint(1, 6)

while(pair_num1 != pair_num2):#두 수가 같지 않다면(True) 계속 반복

    if(pair_num1 &gt; pair_num2):#1이 2보다 크면
        print(f&quot;pair_num1({pair_num1}) 변수의 값이 pair_num2({pair_num2}) 변수의 값보다 크다.&quot;)

    elif(pair_num1 &lt; pair_num2):#1이 2보다 작으면
        print(f&quot;pair_num1({pair_num1}) 변수의 값이 pair_num2({pair_num2}) 변수의 값보다 작다.&quot;)

    else :#이외의 경우 에러 반환
        print(f&quot;Error : pair_num1({pair_num1}), pair_num2({pair_num2})&quot;)

    #난수 재할당
    pair_num1 = random.randint(1, 6)
    pair_num2 = random.randint(1, 6)
    #print(pair_num1, pair_num2) #난수 확인 테스트


print(&quot;게임 끝&quot;)</code></pre><br />

<h3 id="문제-3">문제 3</h3>
<ul>
<li>2번 문제의 소스를 복사해서 <span style="color: red; font-weight: bold;">무한루프를 사용</span>하는 소스로 변경한다.<br /></li>
<li>풀이<pre><code class="language-python"># 3번
import random
</code></pre>
</li>
</ul>
<p>#변수 초기화
pair_num1 = random.randint(1, 6)
pair_num2 = random.randint(1, 6)</p>
<p>while(True):#무한루프</p>
<pre><code>if(pair_num1 &gt; pair_num2):#1이 2보다 크면
    print(f&quot;pair_num1({pair_num1}) 변수의 값이 pair_num2({pair_num2}) 변수의 값보다 크다.&quot;)

elif(pair_num1 &lt; pair_num2):#1이 2보다 작으면
    print(f&quot;pair_num1({pair_num1}) 변수의 값이 pair_num2({pair_num2}) 변수의 값보다 작다.&quot;)

elif(pair_num1 == pair_num2):#1이 2와 같으면 종료
    print(&quot;게임 끝&quot;)
    break

else:#이외의 경우 에러 반환
    print(f&quot;Error : pair_num1({pair_num1}), pair_num2({pair_num2})&quot;)

#난수 재할당
pair_num1 = random.randint(1, 6)
pair_num2 = random.randint(1, 6)
#print(pair_num1, pair_num2) #난수 확인 테스트</code></pre><pre><code>&lt;br&gt;

### 문제 4

- while 문으로 다음 기능을 반복하도록 한다.
- 0부터 30사이의 난수를 추출한다.
  추출된 숫자가 1이면 'A', 2 이면 'B', ... 26이면 'Z' 를 출력하는데
  계속 난수 추출과 출력을 반복하다가 난수가 0이 추출되거나
  27~30이 추출되면 반복을 끝낸다.

  반복하는 동안 출력형식 :&lt;br&gt;      
            &lt;pre&gt;
            B(2)
            A(1)
            D(4)
            :
            &lt;/pre&gt;
- 마지막에는 &quot;수행횟수는 x 번입니다&quot;를 출력하고 종료한다. (수행 횟수는 출력을 기준으로 계산)
&lt;br&gt;
- 풀이
```python
# 4번
import random

#print(chr(65)) #ASCII 확인용 코드

#무한루프 전 반복수 확인 위한 count 변수 할당
count = 0

while(1) :#무한루프
    randnum = random.randint(0, 30) #randnum 변수 값 할당

    if (randnum &gt;= 1 and randnum &lt;= 26) : #1과 26사이의 값
        print(f&quot;{chr(64+randnum)}({randnum})&quot;)
        #count += 1 #반복마다 count 증가시켜 할당, 여기에 넣어도 무방함
    elif(randnum == 0 or (randnum &gt;= 27 and randnum &lt;= 30)):#0이거나 27과 30사이의 값
        print(f&quot;수행횟수는 {count}번입니다.&quot;)
        break #수행 후 무한루프 탈출

    else : #이외의 경우 에러메시지 반환
        print(f&quot;Error - randnum : {randnum}&quot;)

    count += 1 #반복마다 count 증가시켜 할당
</code></pre><ul>
<li>count 증가 시, 위치 선정을 잘 하는게 중요했음<ul>
<li>1과 26사이 값 나올때만 증가시키면 됨</li>
<li>혹은 아예 루프 밖에 빼서 수행,
다시 루프 돌아가는 경우에만 카운트를 진행해준다<br />

</li>
</ul>
</li>
</ul>
<hr />
<h1 id="함수">함수</h1>
<blockquote>
<p>어떤 일을 수행하는 코드의 코드블록 또는 코드의 묶음.</p>
</blockquote>
<hr />
<h3 id="1-함수의-특징">1. 함수의 특징</h3>
<ul>
<li>수학에서의 함수<ul>
<li>두 집합 사이를 설명하는 논리적 개념<br /></li>
</ul>
</li>
<li>프로그래밍에서의 함수<ul>
<li>일정한 동작을 수행하는 코드들의 묶음<br />
### 2. 함수 정의</li>
</ul>
</li>
<li>정의 방법<pre><code class="language-python">#첫 번째
def 함수명() : #함수명 직관적으로, 소괄호 무조건
  함수의 코드블럭
</code></pre>
</li>
</ul>
<p>#두 번째
def 함수명(p1, p2): #p1, p2 : 매개변수
    코드블럭
#변수를 받아서 반환하는 함수</p>
<pre><code>-  주의사항
   - 함수명은 늘 **직관적**으로 구성하도록 !!
   - 열을 맞춰야 한다
&lt;br&gt;
### 3. 함수 사용
- 호출이 필요함
-&gt; 호출식 사용

- 함수명1()
함수명2(10, 20)
  - 받고자 하는 변수의 개수에 맞춰서,
괄호 안에 변수를 나열한다.
  - 10, 20 : **아규먼트**
- 선언 형식
  - 함수명2(v1, v2)
  - 함수명2(v1+1, v2+10)
  - 함수명2(함수명3(),v2)

- p1, p2와 같은 변수는 **매개변수**라고 한다.

- 주의사항
  - 매개변수는 몇 개를 얼마나 정의할지?
  - 함수명은 얼마나 직관적으로 설정할지?

- 함수명, 매개변수, **리턴값(return 값)**
  - 리턴값이 있는 함수로 만들지는 필요에 따라 설정

```python
def 함수명1():
    코드블록

def 함수명2(p1, p2): #p1, p2 : 매개변수
    코드블록
    return p1+p2

result1 = 함수명1()
result2 = 함수명2(100, 200)</code></pre><br />

<h3 id="4-함수-중복">4. 함수 중복</h3>
<ul>
<li>동일한 이름의 함수를 여러 개 만들면, 가장 후순위로 정의된 함수를 사용한다.</li>
</ul>
<h3 id="5-return">5. Return</h3>
<ul>
<li>함수가 return값이 있을 경우, 해당 값은 print처럼 표시될 수도 있다.</li>
<li>다만, 함수가 마지막으로 쓰여야 한다.<ul>
<li>마지막으로 쓰인 함수의 return값은 출력된다.</li>
<li>중간은 사라진다.</li>
</ul>
</li>
</ul>
<h3 id="6-docstring">6. docstring</h3>
<ul>
<li>함수를 정의한 이후, 개행을 여러 줄 써서 함수의 설명을 돕는다. help() 썼을 때 사용정보를 표시해줌.<pre><code class="language-python">def calcsum(n):
  &quot;&quot;&quot;n : 정수형 숫자 
     1 ~ n까지의 합계를 구해 리턴한다.&quot;&quot;&quot;  # docstring
  sum = 0
  for i in range(n+1):
          sum += i
  return sum
</code></pre>
</li>
</ul>
<p>print(calcsum(10))</p>
<pre><code>---
## 문제풀이

&gt;아직 크게 막히는 부분은 없다

### 문제 1
- 구현해야 하는 함수 사양

   함수명 : print_book_title
   매개변수 : 없음
   리턴값 : 없음
   기능 : 파이썬 교재명을 화면에 출력&lt;br&gt;
   함수명 : print_book_publisher
   매개변수 : 없음
   리턴값 : 없음
   기능 : 파이썬 교재의 출판사명을 화면에 출력
- print_book_title() 함수를 3회 호출하고 print_book_publisher() 함수를 5회 호출한다.

- 풀이

```python
# 1번

def print_book_title():
    print(&quot;기초부터 실전까지 한 권에 끝내는 파이썬 프로그래밍&quot;)
def print_book_publisher():
    print(&quot;시대인&quot;)

for i in range(1,4):
    print_book_title()
for i in range(1,6):
    print_book_publisher()</code></pre><h3 id="문제-2">문제 2</h3>
<ul>
<li><p>구현해야 하는 함수 사양</p>
</li>
<li><p>함수명 : get_book_title
 매개변수 : 없음
 리턴값 : 있음
 기능 : 파이썬 교재명을 리턴한다.<br />
 함수명 : get_book_publisher
 매개변수 : 없음
 리턴값 : 있음
 기능 : 파이썬 교재의 출판사명을 리턴한다.</p>
</li>
<li><p>get_book_title() 함수를 호출하고 리턴되는 결과를 name 변수에 저장한 다음 name 변수의 값을 3회 
출력한다.</p>
</li>
<li><p>get_book_publisher() 함수를  호출하고 리턴되는 결과를 바로 화면에 출력하는 처리를 2회한다.</p>
</li>
<li><p>풀이</p>
</li>
</ul>
<pre><code class="language-python"># 2번

def get_book_title():
    return &quot;기초부터 실전까지 한 권에 끝내는 파이썬 프로그래밍&quot;
def get_book_publisher():
    return &quot;시대인&quot;

for i in range(1,4):
    name = get_book_title()
    print(name)
for i in range(1,3):
    print_book_publisher()</code></pre>
<h3 id="문제-3-1">문제 3</h3>
<ul>
<li><p>구현해야 하는 함수 사양</p>
<p> 함수명 : expr
 매개변수 : 숫자 2개와 연산자 1개
 리턴값 : 연산 결과 또는  None
 기능 : 전달된 두 개의 숫자에 대해서 전달된 연산을 처리하고 그 결과를 리턴한다.</p>
<pre><code>    연산자는 +, -, *, / 만 처리하며 그 외의 연산자는 연산을 하지 않고 None 을 리턴한다.&lt;br&gt;</code></pre></li>
<li><p>숫자 2개와 연산자 1개를 전달하여 expr() 이라는 함수를 호출한 다음 리턴 결과가 None 이면
<span style="color: blue;">수행 불가</span> 를 출력하고 그렇지 않으면 <span style="color: blue;">연산결과 : XX</span> 를 출력한다.</p>
</li>
<li><p>풀이</p>
<pre><code class="language-python"># 3번
</code></pre>
</li>
</ul>
<p>#함수 정의
def expr(num1, num2, calc):
    num1 = float(num1)
    num2 = float(num2)</p>
<pre><code>if calc == &quot;+&quot;:
    return num1 + num2
elif calc == &quot;-&quot;:
    return num1 - num2
elif calc == &quot;*&quot;:
    return num1 * num2
elif calc == &quot;/&quot;:
    return num1 / num2
else :
    return &quot;None&quot;</code></pre><p>#input 문
num1 = input(&quot;첫 번째 숫자를 적으세요.&quot;)
num2 = input(&quot;두 번째 숫자를 적으세요.&quot;)
calc =  input(&quot;+, -, *, / 중 연산자를 적으세요.&quot;)</p>
<p>#if문 실행
if expr(num1, num2, calc) == &quot;None&quot;:
    print(&quot;수행 불가&quot;)
else :
    print(f&quot;연산결과 : {expr(num1, num2, calc)}&quot;)</p>
<pre><code>
### 문제 4
- 구현해야 하는 함수 사양

   함수명 : print_triangle
   매개변수 : 1개
   리턴값 : 없음
   기능 : 전달된 숫자 개수로 구성되는 삼각형을 출력한다. 출력 형식은 다음과 같다.&lt;br&gt;
</code></pre><pre><code>     2 전달시&lt;br&gt;
     *
     **
     5 전달시&lt;br&gt;
     *
     **
     ***
     ****
     *****</code></pre><pre><code>
전달되는 아규먼트 값은 1 ~ 10으로 제한한다.&lt;br&gt;
1 ~ 10 이외의 값이 전달된 경우에는 처리하지 않고 그냥 리턴한다.

- 다음 코드로 print_triangle() 함수를 호출해 본다.

      print_triangle(3)
      print_triangle(15)
      print_triangle(6) 

- 풀이
```python
# 4번

#함수 정의
def print_triangle(num):
    if 0 &lt; num and num &lt;= 10 and type(num) == int: #1~10의 정수 전달되었을 경우
        for i in range(1, num+1): #1부터 num행까지 각각 i개의 별을 출력
            print(&quot;*&quot;*i)
            #for j in range(i) :
            #    print(&quot;*&quot;, end = &quot;&quot;)

print_triangle(3)
print_triangle(15)
print_triangle(6)</code></pre><h3 id="문제-5">문제 5</h3>
<ul>
<li><p>구현해야 하는 함수 사양</p>
<p> 함수명 : print_gugudan
 매개변수 : 1개
 리턴값 : 없음
 기능 : 전달된 숫자의 구구단을 출력한다.<br /></p>
<pre><code>    전달된 아규먼트가 int 타입인지 채크하고 int 타입이 아니면 그냥 리턴한다.&lt;br&gt;
    전달된 아규먼트가 1~9 사이인지 채크하고 아니면 그냥 리턴한다.
    그 외의 경우에는 해당 단의 구구단을 행 단위로 출력한다.&lt;br&gt;

          3 x 1 = 3
          3 x 2 - 6
              :                       </code></pre></li>
</ul>
<ul>
<li><p>숫자를 다양하게 지정해서 print_ gugudan() 함수를 호출해 본다.</p>
</li>
<li><p>풀이</p>
<pre><code class="language-python"># 5번
</code></pre>
</li>
</ul>
<p>#함수 정의
def print_gugudan(num):
    if type(num) == int and 0 &lt; num &lt; 10 :
        for i in range(1, 10):
            print(f&quot;{num} X {i} = {num*i}&quot;)
    else :
        return</p>
<p>#for i in range(-2, 11):</p>
<h1 id="print_gugudani">print_gugudan(i)</h1>
<p>#print_gugudan(1.5)</p>
<pre><code>

### 문제 6

- 구현해야 하는 함수 사양

   함수명 : differ_two_value
   매개변수 : 2개
   리턴값 : 연산 결과값
   기능 : 전달받은 2개의 데이터 중에서 큰 값에서 작은 값의 차를 리턴 두 값이 동일하면 0 을 리턴한다.&lt;br&gt;
          예를 들어)
           10, 20 이 전달되면 ---&gt; 10 리턴
           20, 5 가 전달되면 ---&gt; 15 리턴
           5, 30 이 전달되면 ---&gt; 25 리턴
           6, 3 이 전달되면  ---&gt; 3 리턴

- 1부터 30 사이의 난수 2 개를 추출하여 2번에서 구현된 함수를 다섯번호출하고 결과를 다음 형식으로 출력한다.&lt;br&gt;
        X 와 Y 의 차는 W 입니다.
        X 와 Y 의 차는 W 입니다.
        X 와 Y 의 차는 W 입니다.
        X 와 Y 의 차는 W 입니다.
        X 와 Y 의 차는 W 입니다. 

```python
# 6번

import random

#함수 정의
def differ_two_value(num1, num2):
    if type(num1) == int and type(num2) == int:
        return abs(num1 - num2) #절댓값으로 한 번에 계산

#5번 반복문
for i in range(1, 6):
    randnum1 = random.randint(1, 30)
    randnum2 = random.randint(1, 30)
    print(f&quot;{randnum1} 와 {randnum2} 의 차는 {differ_two_value(randnum1, randnum2)} 입니다.&quot;)</code></pre><hr />
<h1 id="자료형">자료형</h1>