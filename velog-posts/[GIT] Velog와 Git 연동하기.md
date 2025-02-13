<h2 id="1-왜-연동하는데">1. 왜 연동하는데?</h2>
<blockquote>
<p>현대로템 부트캠프를 들으면서, 듣는 내용들을 깃에 기록하고 있다. 기초 수업이라 아는 내용이 나오는 동안 시간이 널럴하기 때문에, 기존에 정리하지 못했던 GIT작업을 마무리하려 한다.</p>
</blockquote>
<p>GIT에 계속해서 게시물을 연동하면, 다음과 같은 장점이 있겠다.</p>
<h3 id="1-활동-증빙">1) 활동 증빙</h3>
<p>아무래도 GIT으로 관리하면 매일 얼마나 생산성을 발휘했는지 <strong>잔디</strong>로 알 수 있다. 그래서 이 부분이 편리하다.</p>
<h3 id="2-관리의-편의성">2) 관리의 편의성</h3>
<p>예전에 연구소 근무할 때, Confluence, Jira, Sourcetree, Bitbucket 연동으로 편하게 소프트웨어 형상관리를 진행한 적이 있었다. 마찬가지로 연동이 되어 있으면 형상관리 시 수월한 면이 있다.
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/526b2fb2-ad9f-4298-a11b-db768721d468/image.png" />
<img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/76510417-f380-4bc5-97d1-17cf1ce36b06/image.png" /></p>
<br />

<hr />
<h2 id="2--연동-시도">2.  연동 시도</h2>
<h3 id="1-레퍼런스-참조">1) 레퍼런스 참조</h3>
<p>처음 시작할 때부터 스스로 전부 알아가기보다는,
개발자는 적재적소의 구글링 실력이 중요하다고 생각한다!!!</p>
<p>오픈소스로 올려놓으신 블로그를 참고했다는 뜻이다..
덕분에 잘 마무리 했습니다
감사합니다진짜</p>
<ul>
<li>블로그 주소
<a href="https://velog.io/@ryuneng2/GitHub-velog%EC%99%80-GitHub-%EC%97%B0%EB%8F%99%ED%95%98%EA%B8%B0-velog-%EA%B8%80-%EC%9E%91%EC%84%B1-%EC%8B%9C-%EC%9E%90%EB%8F%99%EC%9C%BC%EB%A1%9C-%EA%B9%83%ED%97%88%EB%B8%8C%EC%97%90-%EC%BB%A4%EB%B0%8B%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95">https://velog.io/@ryuneng2/GitHub-velog와-GitHub-연동하기-velog-글-작성-시-자동으로-깃허브에-커밋하는-방법</a><br />

</li>
</ul>
<h3 id="2-github--repository-생성">2) GitHub &gt; Repository 생성</h3>
<ul>
<li>원문에서는 Public으로 새로운 레포지토리를 생성하셨지만.. 공부용으로 작년에 만들어놓은 레포지토리가 있어 그곳으로 경로를 삼기로 하였다.</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/0b2023fb-069b-4841-8af3-9f60bc376e54/image.png" /></p>
 <br />

<h3 id="3-update_blogyml-파일-생성">3) update_blog.yml 파일 생성</h3>
<blockquote>
<p><strong>GitHub action 작성</strong></p>
</blockquote>
<h4 id="1-creating-a-new-file-파일-경로를-다음과-같이-설정했다">1) Creating a new file, 파일 경로를 다음과 같이 설정했다.</h4>
<p><img alt="" src="https://velog.velcdn.com/images/yookkilhwan/post/8c0107f5-952d-470e-a953-8f25ee65778a/image.png" /></p>
<h4 id="2-내용-작성">2) 내용 작성</h4>
<pre><code class="language-yml">name: Update Blog Posts


on:
  push:
      branches: #1. 브랜치명 설정
        - main  # 또는 워크플로우를 트리거하고 싶은 브랜치 이름
  schedule:
    # 테스트를 원한다면, `한국 표준시 = UTC + 9` 참고해서 시간 수정한 후 테스트해보기
    - cron: '0 0 * * *'  # 매일 자정에 실행, UTC 협정 세계시 기준 (한국 시간 기준 오전 9시)
    - cron: '0 15 * * *' # 매일 자정에 실행, 한국 시간 기준 (UTC 15:00)

jobs:
  update_blog:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Push changes
      run: |
        git config --global user.name 'github-actions[bot]'
        git config --global user.email 'github-actions[bot]@users.noreply.github.com'
        git push https://${{ secrets.GH_PAT }}@github.com/kilhwan6/Algorithm.git #2. 내 깃허브 아이디와 레포지토리 설정

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.x'

    - name: Install dependencies
      run: |
        pip install feedparser gitpython

    - name: Run script
      run: python scripts/update_blog.py</code></pre>
<ul>
<li>3) commit changes로 커밋<br />

</li>
</ul>
<h3 id="4-update_blogpy-파일-생성">4) update_blog.py 파일 생성</h3>
<blockquote>
<p><strong>파이썬 스크립트 작성</strong></p>
</blockquote>
<h4 id="1-파일-경로--scriptsupdate_blogpy">1) 파일 경로 : scripts/update_blog.py</h4>
<ul>
<li>이대로 작성하면 폴더도 자동으로 함께 생성됨<h4 id="2-내용">2) 내용</h4>
<pre><code class="language-python">import feedparser
import git
import os
</code></pre>
</li>
</ul>
<h1 id="벨로그-rss-피드-url">벨로그 RSS 피드 URL</h1>
<h1 id="example--rss_url--httpsapivelogiorssrimgosu">example : rss_url = '<a href="https://api.velog.io/rss/@rimgosu'">https://api.velog.io/rss/@rimgosu'</a></h1>
<p>rss_url = '<a href="https://api.velog.io/rss/@%5B%EB%B3%B8%EC%9D%B8%EB%B2%A8%EB%A1%9C%EA%B7%B8%EC%95%84%EC%9D%B4%EB%94%94%5D'">https://api.velog.io/rss/@[본인벨로그아이디]'</a></p>
<h1 id="깃허브-레포지토리-경로">깃허브 레포지토리 경로</h1>
<p>repo_path = '.'</p>
<h1 id="velog-posts-폴더-경로">'velog-posts' 폴더 경로</h1>
<p>posts_dir = os.path.join(repo_path, 'velog-posts')</p>
<h1 id="velog-posts-폴더가-없다면-생성">'velog-posts' 폴더가 없다면 생성</h1>
<p>if not os.path.exists(posts_dir):
    os.makedirs(posts_dir)</p>
<h1 id="레포지토리-로드">레포지토리 로드</h1>
<p>repo = git.Repo(repo_path)</p>
<h1 id="rss-피드-파싱">RSS 피드 파싱</h1>
<p>feed = feedparser.parse(rss_url)</p>
<h1 id="각-글을-파일로-저장하고-커밋">각 글을 파일로 저장하고 커밋</h1>
<p>for entry in feed.entries:
    # 파일 이름에서 유효하지 않은 문자 제거 또는 대체
    file_name = entry.title
    file_name = file_name.replace('/', '-')  # 슬래시를 대시로 대체
    file_name = file_name.replace('\', '-')  # 백슬래시를 대시로 대체
    # 필요에 따라 추가 문자 대체
    file_name += '.md'
    file_path = os.path.join(posts_dir, file_name)</p>
<pre><code># 파일이 이미 존재하지 않으면 생성
if not os.path.exists(file_path):
    with open(file_path, 'w', encoding='utf-8') as file:
        file.write(entry.description)  # 글 내용을 파일에 작성

    # 깃허브 커밋
    repo.git.add(file_path)
    repo.git.commit('-m', f'Add post: {entry.title}')</code></pre><h1 id="변경-사항을-깃허브에-푸시">변경 사항을 깃허브에 푸시</h1>
<p>repo.git.push()</p>
<pre><code>- 3) Commit changes 클릭해서 커밋
 &lt;br&gt;

### 5) PAT 권한 받기
#### 1) GitHub 계정 -&gt; Settings 클릭
#### 2) Developer Settings 클릭(맨아래)
#### 3) Personal access tokens &gt; Tokens (classic) &gt; Generate new token &gt; Generate new token (classic) 클릭
#### 4) 토큰 이름 작성 &amp; repo, workflow 체크 후 Generate token 클릭
#### 5)  토큰 복사
- 이 창을 벗어나면 이후에는 토큰 확인이 불가하니 꼭 복사 !! 해두기

![](https://velog.velcdn.com/images/yookkilhwan/post/695173f9-b463-47d8-87ab-717d7fa8b432/image.png)

#### 6) velog 리포지토리 &gt; Settings &gt; Secrets and Variables &gt; Actions &gt; New repository secret 클릭

#### 7) Name, Secret 작성 후 Add secret 클릭
- Name : GH_PAT
- Secret : 위에서 복사한 토큰 붙여넣기
 &lt;br&gt;

### 6) 리포지토리에 외부 권한 부여
#### 1) velog 리포지토리 &gt; Settings 클릭
#### 2) Actions &gt; General 클릭
#### 3) 4개 체크 및 Save (각 항목 변경할 때마다 Save도 잊지 말고 눌러주기)
 &lt;br&gt;



### 7) 실패하기

크아아악, 저장소 권한 오류가 발생했다
GitHub Action bot에게도 수정 권한을 부여해보자.
![](https://velog.velcdn.com/images/yookkilhwan/post/a1865089-a3c1-4f8e-b3b9-099d89b8e9bd/image.png)


### 8) 성공
다른 블로그 도움 없었으면 일주일은 걸렸겠다.
![](https://velog.velcdn.com/images/yookkilhwan/post/6343e92a-3109-4b6c-9bf9-d3cbfca6fc54/image.png)
</code></pre>