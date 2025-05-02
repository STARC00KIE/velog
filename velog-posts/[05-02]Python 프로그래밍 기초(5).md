<h1 id="오버라이딩">오버라이딩</h1>
<ul>
<li>부모 클래스에 이미 정의된 메서드를, 자식 클래스에서 '다시' 정의하는 것을 말함
쉽게: 부모가 물려준 함수를 &quot;내 스타일&quot;로 덮어쓰기(override) 하는 것</li>
<li>오버라이딩을 하는 이유<ul>
<li>부모가 물려준 기본 동작이 자식 클래스에 딱 맞지 않을 때, 자식 클래스에 맞게 기능을 바꿔서 쓰기 위해 사용</li>
</ul>
</li>
</ul>
<hr />
<h1 id="아나콘다anaconda">아나콘다(Anaconda)</h1>
<ul>
<li>Python과 R 프로그래밍을 위한 패키지, 환경 관리를 쉽게 해주는 통합 플랫폼</li>
<li>데이터 과학, 머신러닝, 인공지능, 통계 분석을 할 때 필요한 수천 개 라이브러리를 한번에 관리할 수 있음</li>
<li>특히 <strong>가상 환경(virtual environment)</strong>을 만들어서 프로젝트별로 다른 패키지 버전을 사용할 수 있게 도와줌</li>
<li>기본적으로 conda라는 패키지 관리 명령어를 제공합니다.</li>
</ul>
<h2 id="정리">정리:</h2>
<h3 id="아나콘다--패키지-설치--가상환경-관리--데이터-과학에-필요한-기본-툴-모음">아나콘다 = 패키지 설치 + 가상환경 관리 + 데이터 과학에 필요한 기본 툴 모음</h3>
<hr />
<h1 id="아나콘다-환경-관리">아나콘다 환경 관리</h1>
<p>여러 프로젝트를 독립적으로 관리하기 위해 가상환경을 사용합니다.</p>
<ol>
<li><p>가상 환경 만들기</p>
<ul>
<li><code>conda create -n 환경이름 python=버전</code></li>
<li>예시: <code>conda create -n myenv python=3.11</code><ul>
<li>-n 옵션: 새 환경 이름 지정</li>
<li>python=버전: 특정 파이썬 버전으로 환경 생성</li>
</ul>
</li>
</ul>
</li>
<li><p>가상 환경 활성화 (접속)</p>
</li>
</ol>
<ul>
<li><code>conda activate 환경이름</code></li>
<li>예시: <code>conda activate myenv</code><ul>
<li>활성화되면 (myenv) 표시가 명령줄 앞에 생김</li>
</ul>
</li>
</ul>
<ol start="3">
<li>가상 환경 비활성화 (종료)</li>
</ol>
<ul>
<li><code>conda deactivate</code></li>
</ul>
<ol start="4">
<li>가상 환경 삭제</li>
</ol>
<ul>
<li><code>conda remove -n 환경이름 --all</code></li>
<li>예시: <code>conda remove -n myenv --all</code></li>
</ul>
<ol start="5">
<li>가상 환경 목록 보기</li>
</ol>
<ul>
<li><code>conda env list</code> 또는 <code>conda info --envs</code></li>
<li>설치된 가상환경 리스트와 경로를 확인할 수 있습니다.</li>
</ul>
<hr />
<h1 id="패키지-설치">패키지 설치</h1>
<ul>
<li>Anaconda는 conda 명령어로 패키지를 설치합니다.</li>
<li>conda install 패키지이름</li>
<li>예시:<pre><code class="language-python">conda install numpy
conda install pandas</code></pre>
</li>
<li>특정 버전 설치: <code>conda install 패키지이름=버전</code></li>
<li>예시: <code>conda install numpy=1.24</code></li>
<li>여러 패키지 동시 설치: <code>conda install 패키지1 패키지2</code></li>
<li>conda-forge 채널에서 설치 (추천 오픈소스 채널): <code>conda install -c conda-forge 패키지이름</code></li>
<li><code>pip</code> 사용해도 됨</li>
</ul>
<hr />
<h1 id="패키지-관리">패키지 관리</h1>
<ul>
<li>패키지 업데이트: <code>conda update 패키지이름</code></li>
<li>아나콘다 전체 업데이트: <code>conda update anaconda</code></li>
<li>conda 자체 업데이트: <code>conda update conda</code></li>
<li>패키지 삭제: <code>conda remove 패키지이름</code></li>
</ul>
<hr />
<h1 id="설치된-모듈패키지-확인">설치된 모듈(패키지) 확인</h1>
<ul>
<li>현재 환경에 설치된 패키지 목록을 확인할 수 있음</li>
<li><code>conda list</code></li>
<li>특정 패키지 검색:<pre><code class="language-python">conda list | findstr 패키지이름   # (Windows)
conda list | grep 패키지이름      # (Mac/Linux)</code></pre>
</li>
<li>환경별 패키지 확인 (다른 환경에서): <code>conda list -n 환경이름</code></li>
</ul>
<hr />
<h1 id="아나콘다-명령어-요약-표">아나콘다 명령어 요약 표</h1>
<table>
<thead>
<tr>
<th align="left">목적</th>
<th align="left">명령어 예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left">패키지 설치</td>
<td align="left">conda install numpy</td>
</tr>
<tr>
<td align="left">특정 버전 설치</td>
<td align="left">conda install numpy=1.24</td>
</tr>
<tr>
<td align="left">패키지 업데이트</td>
<td align="left">conda update numpy</td>
</tr>
<tr>
<td align="left">패키지 삭제</td>
<td align="left">conda remove numpy</td>
</tr>
<tr>
<td align="left">설치된 패키지 확인</td>
<td align="left">conda list</td>
</tr>
<tr>
<td align="left">특정 환경 패키지 확인</td>
<td align="left">conda list -n myenv</td>
</tr>
</tbody></table>
<hr />
<h1 id="파일-열기">파일 열기</h1>
<ul>
<li>파일을 열 때는 open() 함수를 사용함</li>
<li><code>f = open('파일이름', '모드')</code></li>
<li>'파일이름': 열 파일의 경로와 이름</li>
<li>'모드': 읽기/쓰기/추가 등 파일을 다루는 방법을 지정</li>
<li>파일 열기 후에는 작업이 끝나면 반드시 파일을 닫아야 함 <strong>(메모리 누수 방지)</strong></li>
</ul>
<hr />
<h1 id="파일-닫기">파일 닫기</h1>
<ul>
<li><code>f.close()</code></li>
<li>파일 작업이 끝났으면 꼭 close()를 호출해야 함</li>
<li>파일을 닫지 않으면 데이터가 저장되지 않거나 시스템 리소스가 낭비될 수 있음</li>
<li>사용 예시<pre><code class="language-python">f = open('test.txt', 'r')
내용 = f.read()
print(내용)
f.close()</code></pre>
</li>
</ul>
<hr />
<h1 id="파일을-열고-닫을-때-with문-사용-권장">파일을 열고 닫을 때 with문 사용 권장</h1>
<ul>
<li>파일을 열고 닫는 과정을 자동으로 처리해줌<pre><code class="language-python">with open('파일이름', '모드') as f:
  # 파일 작업
  데이터 = f.read()
  print(데이터)</code></pre>
</li>
<li><code>with</code>를 쓰면 블록이 끝날 때 자동으로 <code>f.close()</code>를 호출함</li>
<li>실수로 파일을 안 닫는 문제를 막을 수 있어 강력 추천함</li>
</ul>
<hr />
<h1 id="파일-열기-접근-모드">파일 열기 접근 모드</h1>
<table>
<thead>
<tr>
<th align="left">모드</th>
<th align="left">의미</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>'r'</code></td>
<td align="left">읽기</td>
<td align="left">파일을 읽기용으로 엶. 파일이 없으면 에러</td>
</tr>
<tr>
<td align="left"><code>'w'</code></td>
<td align="left">쓰기</td>
<td align="left">파일을 쓰기용으로 엶. 파일이 있으면 <strong>내용을 모두 지움</strong></td>
</tr>
<tr>
<td align="left"><code>'a'</code></td>
<td align="left">추가</td>
<td align="left">파일에 내용을 추가. 파일이 없으면 새로 만듦</td>
</tr>
<tr>
<td align="left"><code>'x'</code></td>
<td align="left">생성</td>
<td align="left">파일을 새로 생성. 파일이 이미 있으면 에러</td>
</tr>
<tr>
<td align="left"><code>'b'</code></td>
<td align="left">바이너리</td>
<td align="left">이진(binary) 모드. (예: 이미지, 동영상 파일 열 때 사용)</td>
</tr>
<tr>
<td align="left"><code>'t'</code></td>
<td align="left">텍스트</td>
<td align="left">텍스트 모드 (기본값)</td>
</tr>
<tr>
<td align="left"><code>'+'</code></td>
<td align="left">읽기 + 쓰기</td>
<td align="left">동시에 읽고 쓰기 가능</td>
</tr>
</tbody></table>
<ul>
<li>모드 조합 예시<ul>
<li>'rb' : 바이너리 읽기</li>
<li>'wb' : 바이너리 쓰기</li>
<li>'r+' : 읽고 쓰기</li>
<li>'w+' : 기존 파일 삭제하고 새로 쓰기 + 읽기</li>
<li>'a+' : 기존 내용에 추가하면서 읽고 쓰기</li>
</ul>
</li>
</ul>
<hr />
<h1 id="관련-예제">관련 예제</h1>
<ul>
<li><p>파일 읽기 (r)</p>
<pre><code class="language-python">with open('example.txt', 'r') as f:
  data = f.read()
  print(data)</code></pre>
</li>
<li><p>파일 쓰기 (w)</p>
<pre><code class="language-python">with open('example.txt', 'w') as f:
  f.write(&quot;Hello, World!&quot;)
# 기존 내용이 모두 지워지고 &quot;Hello, World!&quot;만 저장됨</code></pre>
</li>
<li><p>파일 추가쓰기 (a)</p>
<pre><code class="language-python">with open('example.txt', 'a') as f:
  f.write(&quot;\nNew Line&quot;)
# 기존 내용 뒤에 &quot;\nNew Line&quot;이 추가됨</code></pre>
</li>
</ul>
<hr />
<h1 id="파일-열기-관련-기능-정리">파일 열기 관련 기능 정리</h1>
<table>
<thead>
<tr>
<th align="left">기능</th>
<th align="left">사용법</th>
</tr>
</thead>
<tbody><tr>
<td align="left">파일 열기</td>
<td align="left">f = open('파일이름', '모드')</td>
</tr>
<tr>
<td align="left">파일 닫기</td>
<td align="left">f.close()</td>
</tr>
<tr>
<td align="left">안전하게 열기/닫기</td>
<td align="left">with open('파일이름', '모드') as f:</td>
</tr>
<tr>
<td align="left">읽기 모드</td>
<td align="left">'r'</td>
</tr>
<tr>
<td align="left">쓰기 모드</td>
<td align="left">'w'</td>
</tr>
<tr>
<td align="left">추가 모드</td>
<td align="left">'a'</td>
</tr>
<tr>
<td align="left">바이너리 모드</td>
<td align="left">'b' 추가해서 사용 ('rb', 'wb' 등)</td>
</tr>
</tbody></table>
<hr />
<h1 id="문자열--반복-처리-함수-5종">문자열 / 반복 처리 함수 5종</h1>
<table>
<thead>
<tr>
<th align="left">함수</th>
<th align="left">설명</th>
<th align="left">사용 예시</th>
<th align="left">결과</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>split()</code></td>
<td align="left">문자열을 나누어 리스트로 변환</td>
<td align="left"><code>&quot;a b c&quot;.split()</code></td>
<td align="left"><code>['a', 'b', 'c']</code></td>
</tr>
<tr>
<td align="left"><code>strip()</code></td>
<td align="left">문자열 양쪽 끝 공백/문자 제거</td>
<td align="left"><code>&quot;  hello  &quot;.strip()</code></td>
<td align="left"><code>&quot;hello&quot;</code></td>
</tr>
<tr>
<td align="left"><code>map()</code></td>
<td align="left">모든 요소에 함수 적용</td>
<td align="left"><code>list(map(int, ['1', '2']))</code></td>
<td align="left"><code>[1, 2]</code></td>
</tr>
<tr>
<td align="left"><code>join()</code></td>
<td align="left">리스트 요소를 문자열로 연결</td>
<td align="left"><code>' '.join(['a', 'b'])</code></td>
<td align="left"><code>&quot;a b&quot;</code></td>
</tr>
<tr>
<td align="left"><code>filter()</code></td>
<td align="left">조건을 만족하는 요소만 선택</td>
<td align="left"><code>list(filter(lambda x: x&gt;2, [1,2,3,4]))</code></td>
<td align="left"><code>[3, 4]</code></td>
</tr>
</tbody></table>
<hr />
<h1 id="lambda-함수">lambda 함수</h1>
<ul>
<li>lambda는 <strong>&quot;간단한 함수를 한 줄로 만드는 문법&quot;</strong></li>
<li>이름 없는 익명 함수를 만들 때 사용함</li>
<li>보통 짧고 간단한 함수를 빠르게 만들 때 사용함</li>
<li><code>lambda 매개변수들 : 표현식</code></li>
<li>매개변수들 → 함수의 입력</li>
<li>표현식    → 반환할 값 (return 키워드 없음)</li>
</ul>
<hr />
<h1 id="유클리디안-거리-euclidean-distance">유클리디안 거리 (Euclidean Distance)</h1>
<ul>
<li><ol>
<li>기본 개념</li>
</ol>
</li>
<li><p>유클리디안 거리는 두 점 사이의 &quot;<strong>직선 거리</strong>&quot;를 의미함</p>
</li>
<li><p>가장 <strong>일반적인 거리 계산 방법</strong>함</p>
</li>
<li><p>2차원, 3차원뿐만 아니라 고차원에서도 사용함</p>
</li>
<li><ol start="2">
<li>수학적 공식</li>
</ol>
</li>
<li><p>2차원 평면에서 두 점 (x₁, y₁)과 (x₂, y₂) 사이의 거리 공식:</p>
</li>
</ul>
<p>$$
d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}
$$</p>
<ul>
<li>3차원:</li>
</ul>
<p>$$
d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2 + (z_2 - z_1)^2}
$$</p>
<ul>
<li>n차원 일반화:</li>
</ul>
<p>$$
d = \sqrt{ \sum_{i=1}^{n} (p_i - q_i)^2 }
$$</p>
<ul>
<li>여기서 ( p_i, q_i )는 각각 두 점의 i번째 좌표</li>
</ul>
<ol start="3">
<li>간단한 예시</li>
</ol>
<ul>
<li>2차원 예제</li>
<li>두 점 (1, 2), (4, 6) 사이 거리 계산:</li>
</ul>
<p>$$
d = \sqrt{(4-1)^2 + (6-2)^2} = \sqrt{9+16} = \sqrt{25} = 5
$$</p>
<ol start="4">
<li>파이썬 코드 예제</li>
</ol>
<ul>
<li>직접 구현<pre><code class="language-python">def euclidean_distance(p1, p2):
  return sum((a - b) ** 2 for a, b in zip(p1, p2)) ** 0.5
</code></pre>
</li>
</ul>
<h1 id="예시">예시</h1>
<p>p1 = (1, 2)
p2 = (4, 6)
print(euclidean_distance(p1, p2))  </p>
<h1 id="결과-50">결과: 5.0</h1>
<p>```</p>
<h1 id="class-내부에서-self메서드-매서드-차이">class 내부에서 self.메서드(), 매서드() 차이</h1>
<table>
<thead>
<tr>
<th align="left">상황</th>
<th align="left">쓰는 방법</th>
</tr>
</thead>
<tbody><tr>
<td align="left">클래스 안에서, <strong>메서드 부를 때</strong></td>
<td align="left"><code>self.메서드이름(인자)</code></td>
</tr>
<tr>
<td align="left">클래스 밖이나, <strong>독립 함수 부를 때</strong></td>
<td align="left"><code>함수이름(인자)</code></td>
</tr>
</tbody></table>
<ul>
<li>클래스 안에서 self를 사용해야 하나?&quot;를 먼저 생각 한다음 self를 적어줄지 말지 선택하기</li>
</ul>