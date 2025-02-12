<h3 id="1-swea-1225-암호생성기-풀던-중">1. SWEA 1225 암호생성기 풀던 중..</h3>
<p>결과값이 1 0 0 2 0 3 과 같이, 중간에 공백이 포함된 글자를 출력하는 것인데 이를 반복문으로 공백처리해서 출력할 수 있겠지만, output문을 간결하게 하고 싶었다.
String에 한번에 넣으려고 하는 과정에서 조사하게 되었당.
<br /><br /></p>
<h3 id="2-string-클래스의-특징">2. String 클래스의 특징</h3>
<ul>
<li>c : char*, char[]의 형태로 문자열 취급</li>
<li>c++ : 문자열을 하나의 변수 타입으로 사용, 문자열을 다양하고 쉽게 다룰 수 있게 해준다.</li>
<li><blockquote>
<p>char*, char[]와 다르게 문자열 끝에 &quot;\0&quot;문자가 없으며 문자열의 길이를 동적으로 변경이 가능함!!
<br /><br /></p>
</blockquote>
<h3 id="3-string-클래스의-입출력">3. String 클래스의 입출력</h3>
c++ 입출력 방법인 <strong>cin, cout</strong>으로 입출력이 가능하다. <strong>getline함수</strong>도 이용이 가능하다! 
C에서 사용하던 scanf, printf는 사용이 불가능하다.</li>
</ul>
<table>
<thead>
<tr>
<th>함수</th>
<th>기능</th>
</tr>
</thead>
<tbody><tr>
<td>string str;</td>
<td>빈 문자열 str 생성</td>
</tr>
<tr>
<td>string str = &quot;abcdef&quot;;</td>
<td>&quot;abcdef&quot; 로 선언된 str 생성</td>
</tr>
<tr>
<td>string str; str = &quot;abcdef&quot;</td>
<td>&quot;abcdef&quot; 로 선언된 str 생성</td>
</tr>
<tr>
<td>string str2(str1);</td>
<td>str1 문자열을 복사한 str2 생성</td>
</tr>
<tr>
<td>char s[ ] = {'a', 'b', 'c', 'd', 'e', 'f'}; string str(s);</td>
<td>C에서의 문자열과 호환 가능</td>
</tr>
<tr>
<td>string *str = new string(&quot;abcdef&quot;);</td>
<td>new를 이용한 동적할당</td>
</tr>
</tbody></table>
<p><br /><br /></p>
<h3 id="4-string-클래스의-연산자-활용">4. String 클래스의 연산자 활용</h3>
<p>&lt;, &gt;, ==, + 등과 같은 연산자를 사용할 수 있다.</p>
<ul>
<li><strong>문자열 비교 (&lt;, &gt;, ==)</strong> : 두 문자열의 사전 순서를 비교, 또는 동일 여부를 확인할 수 있다.</li>
<li><strong>문자열 연결(+)</strong> : 두 문자열을 이어주는 역할을 한다.</li>
</ul>
<pre><code class="language-cpp">string str1 = &quot;abcdef&quot;;
string str2 = &quot;bbbbbb&quot;;
string str3 = &quot;aaaa&quot;;
string str4 = &quot;abcdef&quot;;
cout &lt;&lt; (str1 &lt; str2) &lt;&lt; ' ' &lt;&lt; (str1 &lt; str3) &lt;&lt; ' ' &lt;&lt; (str1 == str4);
//1 : true , 0 : false

str1 += &quot;A&quot;;
cout &lt;&lt; str1 &lt;&lt; '\n';
str1 = str1 + str2;
cout &lt;&lt; str1 &lt;&lt; '\n';
출처: https://rebro.kr/53 [Rebro의 코딩 일기장:티스토리]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/99753dd4-3d12-4ddf-b16f-bf0f2e1b4ba7/image.png" /></p>
<p>str1보다 str2가 사전 순서가 더 느리기 때문에 true(1)를 반환, str3은 사전 순서가 str1보다 더 빠르기 때문에 false(0)를 반환, str1과 str4는 문자열이 동일하기 때문에 true(1)를 반환하는 것을 볼 수 있다.
또 str1에 &quot;A&quot;를 더해주게 되면 &quot;A&quot;가 str1 맨 뒤에 붙게 되고, str2를 더해주면 str2가 str1의 맨 뒤에 붙게 되는 것도 볼 수 있다.
이처럼 C에서의 문자열보다 훨씬 간편하게 두 문자열에 대한 연산을 할 수 있다.
<br /><br /></p>
<h3 id="5-string-클래스의-멤버-함수">5. String 클래스의 멤버 함수</h3>
<h4 id="string의-특정-원소-접근">String의 특정 원소 접근</h4>
<table>
<thead>
<tr>
<th>함수</th>
<th>기능</th>
</tr>
</thead>
<tbody><tr>
<td>str.at(index)</td>
<td>index 위치의 문자 반환. 유효한 범위인지 체크 O</td>
</tr>
<tr>
<td>str[index]</td>
<td>index 위치의 문자 반환, 유효한 범위인지 체크 X. 따라서 at 함수보다 접근이 빠름</td>
</tr>
<tr>
<td>str.front()</td>
<td>문자열의 가장 앞 문자 반환</td>
</tr>
<tr>
<td>str.back()</td>
<td>문자열의 가장 뒤 문자 반환</td>
</tr>
<tr>
<td><br /><br /></td>
<td></td>
</tr>
<tr>
<td>#### String의 크기</td>
<td></td>
</tr>
<tr>
<td>함수</td>
<td>기능</td>
</tr>
<tr>
<td>---</td>
<td>---</td>
</tr>
<tr>
<td>str.length()</td>
<td>문자열 길이 반환</td>
</tr>
<tr>
<td>str.size()</td>
<td>문자열 길이 반환 (length와 동일)</td>
</tr>
<tr>
<td>str.capacity()</td>
<td>문자열이 사용중인 메모리 크기 반환</td>
</tr>
<tr>
<td>str.resize(n)</td>
<td>string을 n의 크기로 만듬. 기존의 문자열 길이보다 n이 작다면 남은 부분은 삭제하고, n이 크다면 빈 공간으로 채움</td>
</tr>
<tr>
<td>str.resize(n, 'a')</td>
<td>n이 string의 길이보다 더 크다면, 빈 공간을 'a'로 채움</td>
</tr>
<tr>
<td>str.shrink_to_fit</td>
<td>str의 capacity가 실제 사용하는 메모리보다 큰 경우 낭비되는 메모리가 없도록 메모리를 줄여줌</td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td><br /><br /></td>
<td></td>
</tr>
<tr>
<td>#### String에 삽입, 추가, 삭제</td>
<td></td>
</tr>
<tr>
<td>함수</td>
<td>기능</td>
</tr>
<tr>
<td>---</td>
<td>---</td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td><br /><br /></td>
<td></td>
</tr>
<tr>
<td>#### 기타 유용한 String 멤버 함수</td>
<td></td>
</tr>
<tr>
<td>함수</td>
<td>기능</td>
</tr>
<tr>
<td>---</td>
<td>---</td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
</tr>
</tbody></table>