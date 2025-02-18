<h1 id="문제풀이--ex8">문제풀이 : EX8</h1>
<hr />
<br />

<h3 id="문제-1">문제 1</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/ab896c1a-f53a-45dd-8bfa-aff409d15a2e/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 1번
</code></pre>
</li>
</ul>
<p>listv = [ 'p', 'y', 't', 'h', 'o', 'n' ]</p>
<p>#(1)
v1, v2, v3, v4, v5, v6 = listv
#print(f&quot;v1 : {v1}, v2 : {v2}, v3 : {v3}, v4 : {v4}, v5 : {v5}, v6 : {v6}&quot;)
print(v1)
print(v2)
print(v3)
print(v4)
print(v5)
print(v6)</p>
<p>#(2)
print(*listv)</p>
<p>#(3)
print(listv)</p>
<pre><code>
- 결과
```css
p
y
t
h
o
n
p y t h o n
['p', 'y', 't', 'h', 'o', 'n']</code></pre><br />

<h3 id="문제-2">문제 2</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/ef9b0c83-eb59-4649-9885-d62e5636addb/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 2번
</code></pre>
</li>
</ul>
<p>def sum_even(*p):
    sum = 0
    if len(p) == 0 :
        return -1
    else:
        for data in p:
            if type(data) == int and data &gt;= 1 and data%2 == 0 :
                sum += data
        return sum</p>
<p>#test code
print(sum_even())
print(sum_even(1 ,3 , 5))
print(sum_even(-1))
print(sum_even(2, 4))
print(sum_even(1, 2, 3, 4, 5))</p>
<pre><code>- 결과
```css
-1
0
0
6
6</code></pre><br />

<h3 id="문제-3">문제 3</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/95d0074e-568d-426e-953a-5925fa87db92/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 3번
</code></pre>
</li>
</ul>
<p>def sum_num(*p):</p>
<pre><code>sum = 0
no_num_flag = True

if len(p) == 0 :
    return None
else:
    for data in p:
        if type(data) == float :
            no_num_flag = False
            sum += data
    if no_num_flag == False :
        return sum
    else :
        return None</code></pre><p>#test code
print(sum_num(0, 1, 2))
print(sum_num())
print(sum_num(&quot;a&quot;, &quot;b&quot;, &quot;c&quot;))
print(sum_num(0))
print(sum_num(-10, 0, 2, &quot;a&quot;))</p>
<pre><code>
- 결과
```css
3
None
None
0
-8</code></pre><br />

<hr />
<h1 id="가변-매개변수">가변 매개변수</h1>
<blockquote>
<p>여러 개의 변수를 갯수 정해놓지 않고 받는 변수.
<em>가 1개면 위치 변수, *</em>이면 키워드 변수</p>
</blockquote>
<h2 id="1-가변-매개변수-특징">1. 가변 매개변수 특징</h2>
<h3 id="args_tuple-args_dict-차이">args_tuple, args_dict 차이</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/a90fe72f-a3ba-49e5-b065-161e53788409/image.png" />
<br /></p>
<h2 id="2-keyword">2. **(Keyword)</h2>
<h3 id="문제-예시">문제 예시</h3>
<pre><code class="language-python">def calcstep(**args):
    print(type(args))
    if len(args) == 0 :
        return
    begin = args.get('begin', 1)
    end = args.get('end', 10)
    step = args.get('step', 1)

    sum = 0
    for num in range(begin, end + 1, step):
        sum += num
    return sum

#test code
print(&quot;3 ~ 5 =&quot;, calcstep(begin=3, end=5, step=1))
print(&quot;3 ~ 5 =&quot;, calcstep(step=1, end=5, begin=3))
calcstep()
print(&quot;1 ~ 10 =&quot;, calcstep(p1=1, p2=10, p3=1))
print(&quot;3 ~ 5 =&quot;, calcstep(3, 5, 1)) # TypeError: calcstep() takes 0 positional arguments but 3 were given</code></pre>
<ul>
<li>결과<pre><code class="language-css">&lt;class 'dict'&gt;
3 ~ 5 = 12
&lt;class 'dict'&gt;
3 ~ 5 = 12
&lt;class 'dict'&gt;
&lt;class 'dict'&gt;
1 ~ 10 = 55
TypeError: calcstep() takes 0 positional arguments but 3 were given</code></pre>
</li>
</ul>
<h3 id="특징">특징</h3>
<ul>
<li>기본값이 딕셔너리 형식으로 주어져야 함.</li>
<li>아규먼트 이름이 키워드와 같지 않더라도, 유니크하게만 준다면 호환이 이루어짐</li>
</ul>
<h3 id="혼합-사용">혼합 사용</h3>
<ul>
<li>그냥 아규먼트, 튜플 타입 아규먼트, 딕셔너리 타입 아규먼트는 혼합해서 사용할 수 있다!<ul>
<li>이 때, 각 아규먼트의 선언이 명확하면 그대로 입력받고, 아니면 순서대로 입력받는다.<br />

</li>
</ul>
</li>
</ul>
<hr />
<h1 id="파이썬의-변수-스코프">파이썬의 변수 스코프</h1>
<blockquote>
<p>변수가 어디까지 유효한지 확인해 주는 방법
<strong>언제 어디서</strong> 사용이 가능한지 표시해 준다!
<br /></p>
</blockquote>
<h2 id="1-스코프-종류">1. 스코프 종류</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/d058c070-5504-4aca-a5a3-2bd4dcabb415/image.png" /></p>
<h3 id="빌트인-스코프built-in-scope">빌트인 스코프(Built-in Scope)</h3>
<ul>
<li>파이썬 실행환경에서 항상 포함되는 광범위한 스코프<ul>
<li>파이썬이 내장한 스코프</li>
</ul>
</li>
<li>별다른 선언 없이 항상 사용 가능한 내장 함수<ul>
<li>len(), input(), print()</li>
</ul>
</li>
</ul>
<h3 id="전역-스코프global-scope">전역 스코프(Global Scope)</h3>
<ul>
<li>전역 범위는 코드의 가장 바깥쪽에 정의된 변수들</li>
<li>전역 변수는 모든 함수에서 접근 가능<ul>
<li>함수 내에서 전역 변수를 수정하려면 global 키워드 사용<h3 id="지역-스코프local-scope">지역 스코프(Local Scope)</h3>
</li>
</ul>
</li>
<li>함수 내에서 정의된 변수들을 말한다.</li>
<li>함수 내에서 정의된 변수는 해당 함수 내에서만 접근 가능</li>
<li>파이썬은 블록 스코프를 지원하지 않으며, 지역 스코프로 간주된다<br />

</li>
</ul>
<h2 id="2-스코프-사용">2. 스코프 사용</h2>
<h3 id="지역변수의-함수-외부-호출-불가">지역변수의 함수 외부 호출 불가</h3>
<pre><code class="language-python">def f1():
    print(&quot;In Function-v1:&quot;, v1) # NameError: name 'v1' is not defined
    v2 = 20
    print(&quot;In Function-v2:&quot;, v2)
print(&quot;Out Function-v2:&quot;, v2) # NameError: name 'v2' is not defined</code></pre>
<pre><code class="language-css">NameError                                 Traceback (most recent call last)
Cell In[25], line 1
----&gt; 1 print(&quot;Out Function-v2:&quot;, v2)

NameError: name 'v2' is not defined</code></pre>
<ul>
<li>함수 외부에서도 접근하게 하려면,
global로 전역 변수로 선언 필요<br />

</li>
</ul>
<hr />
<h1 id="문제풀이---ex9">문제풀이 - EX9</h1>
<h3 id="문제-1-1">문제 1</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/0e00a7aa-9a1b-4ad8-b865-9f9c32178d0a/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 1번
</code></pre>
</li>
</ul>
<p>def mydict(**p):
    dic = { }</p>
<pre><code>if len(p) == 0 :
    return dic

for key, value in p.items():
    update_key = &quot;my&quot;+key
    update_val = value
    dic.update({update_key : update_val})
return dic</code></pre><p>#testcode
mydict( b=2, c=3, d=4, e=5, f=6)
mydict( ab=2, df=3, sd=4, e=5, f=6)</p>
<pre><code>- 결과
``` css
{'myab': 2, 'mydf': 3, 'mysd': 4, 'mye': 5, 'myf': 6}</code></pre><br />

<h3 id="문제-2-1">문제 2</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/5956ac8b-8a44-4797-a767-da1650eb1787/image.png" /></p>
<ul>
<li>풀이<pre><code class="language-python"># 2번
</code></pre>
</li>
</ul>
<p>def myprint(<em>p1, *</em>p2):
    deco = &quot;#&quot;
    sep_val = &quot;,&quot;</p>
<pre><code>if len(p1) == 0 and len(p2) == 0:
    print(&quot;Hello Python&quot;)

else :
    print(deco, end = &quot;&quot;)
    for i in range (0, len(p1)):
        if i == len(p1)-1 :
            print(p1[i], end = &quot;&quot;)
        else :
            print(p1[i], end = sep_val)
    print(deco)</code></pre><p>#testcode
myprint(10, 20, 30, deco=&quot;@&quot;, sep=&quot;-&quot;)
myprint(&quot;python&quot;, &quot;javascript&quot;, &quot;R&quot;, deco=&quot;+&quot;)
myprint(&quot;가&quot;, &quot;나&quot;, &quot;다&quot;)
myprint(100)
myprint(True, 111, False, &quot;abc&quot;, deco=&quot;&amp;&quot;, sep=&quot;&quot;)
myprint()</p>
<pre><code>- 결과
```css
#10,20,30#
#python,javascript,R#
#가,나,다#
#100#
#True,111,False,abc#
Hello Python</code></pre><br />

<hr />
<h1 id="파이썬의-oop-프로그래밍">파이썬의 OOP 프로그래밍</h1>
<h2 id="1-객체지향-프로그래밍">1. 객체지향 프로그래밍</h2>
<ul>
<li>프로그램을 개발할 때, 실제 세상에 가깝게 모델링 하는 기법</li>
<li>컴퓨터가 수행하는 작업을 객체들 사이의 상호작용으로 표현</li>
<li>클래스(class)나 객체(object)들의 집합으로 소프트웨어를 개발하자는 개념<ul>
<li>어떤 객체가 필요한지에 따라 클래스를 만든다.</li>
</ul>
</li>
<li>Java, Python, C++, C#, Swift등 현재 사용중인 많은 프로그래밍 언어에서 채택</li>
</ul>
<h2 id="2-클래스">2. 클래스</h2>
<ul>
<li><p>클래스 생성</p>
<pre><code class="language-python">class Friend:    
  def __init__(self, name, age): 
      self.name = name
      self.age = age

  def eat(self, food): 
      print(f&quot;{food}를 먹어요~~~&quot;) </code></pre>
</li>
<li><p>객체 생성
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/a9b1e926-cbc2-4d15-b99a-d17bcec4260a/image.png" /></p>
</li>
</ul>
<ul>
<li><p>private 멤버 정의
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/99fff4ca-2825-4ffc-a516-04a6093009e9/image.png" /></p>
</li>
<li><p>self 변수</p>
<ul>
<li>self변수는 해당 클래스 위치를 알려줌.</li>
</ul>
</li>
</ul>
<pre><code class="language-python">class SelfTest:
    def __init__(self):
        print(&quot;생성자 호출시 self 변수에 전달되는 값 :&quot;, self)
    def m1(self):
        print(&quot;m1() 호출시 self 변수에 전달되는 값 :&quot;, self)
    def m2(self):
        print(&quot;m2() 호출시 self 변수에 전달되는 값 :&quot;, self)

obj1 = SelfTest()
print(&quot;obj1이 참조하는 객체 :&quot;, obj1)
obj1.m1()
obj1.m2()</code></pre>
<ul>
<li>결과</li>
</ul>
<pre><code class="language-css">생성자 호출시 self 변수에 전달되는 값 : &lt;__main__.SelfTest object at 0x000001C09A001580&gt;
obj1이 참조하는 객체 : &lt;__main__.SelfTest object at 0x000001C09A001580&gt;
m1() 호출시 self 변수에 전달되는 값 : &lt;__main__.SelfTest object at 0x000001C09A001580&gt;
m2() 호출시 self 변수에 전달되는 값 : &lt;__main__.SelfTest object at 0x000001C09A001580&gt;</code></pre>
<h2 id="3-call-특수-메서드">3. <strong>call</strong> 특수 메서드</h2>
<ul>
<li>허깅페이스에 올려진 사전학습 AI 모델 사용 시,
그리고 AI 관련 라이브러리 사용 시 많이 사용되는 구문</li>
<li><strong>객체도 함수처럼 호출</strong>할 수 있게 하는 메서드</li>
</ul>
<pre><code class="language-python">class Test:
    def __call__(self, x):
        return x**2

obj = Test()
print(obj(5))</code></pre>
<pre><code class="language-css">25</code></pre>
<ul>
<li>call 메서드가 구현되어서, obj 변수에 함수처럼 붙여넣을 수 있음</li>
</ul>
<pre><code class="language-python">class Counter:
    def __init__(self):
        self.count = 0
    def __call__(self):
        self.count += 1
        return self.count

c = Counter()
print(c()) 
print(c())  
print(c()) </code></pre>
<pre><code class="language-css">1
2
3</code></pre>
<ul>
<li>call 메서드로 인해 호출할 때마다 해당 구문 내 함수가 실행됨.</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/5be6c41e-b80f-4642-b6aa-9edcfea502e1/image.png" /></p>