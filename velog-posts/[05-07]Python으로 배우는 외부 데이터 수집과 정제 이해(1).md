<h1 id="람다-함수">람다 함수</h1>
<ul>
<li>익명 함수를 한 줄로 간단하게 만드는 방법</li>
<li>함수를 한 줄로 표현할 때 사용</li>
<li>주로 map/filter와 같이 사용</li>
</ul>
<hr />
<h1 id="기본-문법">기본 문법</h1>
<ul>
<li><code>lambda 매개변수: 표현식</code></li>
</ul>
<hr />
<h1 id="예제1">예제1</h1>
<ul>
<li><code>add_lambda = lambda x, y: x + y</code></li>
<li><code>print(add(3,4)) # 7</code></li>
</ul>
<hr />
<h1 id="예제2">예제2</h1>
<ul>
<li><code>print((lambda x, y: x * y)(5, 6))  # 30</code></li>
</ul>
<hr />
<h1 id="map-함수">map() 함수</h1>
<ul>
<li>리스트(또는 반복 가능한 것)의 모든 요소에, 특정 함수를 적용해서 새 결과를 만들어 주는 함수</li>
<li>리스트 안의 모든 값에 똑같이 어떤 작업을 하고 싶을 때 반복문 없이 깔끔하게 처리할 수 있음</li>
</ul>
<hr />
<h1 id="기본-문법-1">기본 문법</h1>
<ul>
<li><code>map(함수, 반복 가능한 객체)</code></li>
<li><code>함수</code>에 <code>def</code>함수나 <code>lambda</code>함수 둘 다 가능</li>
<li><code>map()</code>은 반복자(iterator)를 반환하기 때문에 바로 보려면 <code>list()</code>로 감싸야 함</li>
</ul>
<hr />
<h1 id="예제">예제</h1>
<pre><code class="language-python"># for문 버전
result = []
for x in numbers:
    result.append(x * 2)

# map 버전
result = list(map(lambda x: x * 2, numbers))</code></pre>
<ul>
<li><code>for</code> 문을 사용했을 때보다 더욱 간단함</li>
</ul>
<hr />
<h1 id="try---except-문">try - except 문</h1>
<ul>
<li>프로그램이 에러 때문에 멈추지 않게, 에러(예외)를 잡아서 처리하는 방법</li>
<li>try 문에 에러가 발생했을 때 except 문 실행<pre><code class="language-python">try:
  # 에러가 날 수도 있는 코드
except 에러종류 as e:
  # 에러가 났을 때 실행할 코드
  # e에 에러 메세지 담김
finally:
  # 항상 마지막에 실행, 선택사항임</code></pre>
</li>
</ul>
<hr />
<h1 id="numpy">Numpy</h1>
<ul>
<li>Numerical Python의 줄임말</li>
<li>고속 수치 계산과 다차원 배열(행렬) 처리를 위한 파이썬 라이브러리</li>
<li><code>pip install numpy</code>로 설치</li>
<li><code>import numpy as np</code></li>
</ul>
<hr />
<h1 id="numpy-주요-메서드">Numpy 주요 메서드</h1>
<table>
<thead>
<tr>
<th align="left">메서드/속성</th>
<th align="left">설명</th>
<th align="left">예시</th>
<th align="left">간단한 결과</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>np.array()</code></td>
<td align="left">리스트나 튜플을 NumPy 배열로 변환함</td>
<td align="left"><code>np.array([1, 2, 3])</code></td>
<td align="left"><code>[1 2 3]</code></td>
</tr>
<tr>
<td align="left"><code>np.zeros(shape)</code></td>
<td align="left">주어진 크기의 배열을 0으로 채워서 생성함</td>
<td align="left"><code>np.zeros((2, 3))</code></td>
<td align="left"><code>[[0. 0. 0.], [0. 0. 0.]]</code></td>
</tr>
<tr>
<td align="left"><code>np.ones(shape)</code></td>
<td align="left">주어진 크기의 배열을 1로 채워서 생성함</td>
<td align="left"><code>np.ones((2, 2))</code></td>
<td align="left"><code>[[1. 1.], [1. 1.]]</code></td>
</tr>
<tr>
<td align="left"><code>np.eye(N)</code></td>
<td align="left">단위행렬(대각선 1, 나머지 0인 정방행렬)을 생성함</td>
<td align="left"><code>np.eye(3)</code></td>
<td align="left"><code>[[1. 0. 0.], [0. 1. 0.], [0. 0. 1.]]</code></td>
</tr>
<tr>
<td align="left"><code>np.arange(start, stop, step)</code></td>
<td align="left">시작~끝까지 지정한 간격으로 숫자 배열 생성함</td>
<td align="left"><code>np.arange(0, 10, 2)</code></td>
<td align="left"><code>[0 2 4 6 8]</code></td>
</tr>
<tr>
<td align="left"><code>np.linspace(start, stop, num)</code></td>
<td align="left">구간을 균등하게 나눈 숫자 배열 생성함</td>
<td align="left"><code>np.linspace(0, 1, 5)</code></td>
<td align="left"><code>[0.   0.25 0.5  0.75 1.  ]</code></td>
</tr>
<tr>
<td align="left"><code>shape</code></td>
<td align="left">배열의 형태(행, 열 등)를 반환함</td>
<td align="left"><code>a.shape</code></td>
<td align="left"><code>(2, 3)</code></td>
</tr>
<tr>
<td align="left"><code>ndim</code></td>
<td align="left">배열의 차원 수를 반환함</td>
<td align="left"><code>a.ndim</code></td>
<td align="left"><code>2</code></td>
</tr>
<tr>
<td align="left"><code>size</code></td>
<td align="left">배열 전체 원소 개수를 반환함</td>
<td align="left"><code>a.size</code></td>
<td align="left"><code>6</code></td>
</tr>
<tr>
<td align="left"><code>dtype</code></td>
<td align="left">배열의 데이터 타입을 반환함</td>
<td align="left"><code>a.dtype</code></td>
<td align="left"><code>dtype('int64')</code></td>
</tr>
<tr>
<td align="left"><code>reshape(new_shape)</code></td>
<td align="left">배열 형태를 원하는 모양으로 변경함</td>
<td align="left"><code>a.reshape(3, 2)</code></td>
<td align="left">(3행 2열 배열)</td>
</tr>
<tr>
<td align="left"><code>ravel()</code></td>
<td align="left">다차원 배열을 1차원 배열로 변환함 (원본 연결)</td>
<td align="left"><code>a.ravel()</code></td>
<td align="left"><code>[1 2 3 4 5 6]</code></td>
</tr>
<tr>
<td align="left"><code>flatten()</code></td>
<td align="left">다차원 배열을 1차원 배열로 변환함 (복사본)</td>
<td align="left"><code>a.flatten()</code></td>
<td align="left"><code>[1 2 3 4 5 6]</code></td>
</tr>
<tr>
<td align="left"><code>np.sum()</code></td>
<td align="left">배열 원소들의 합을 계산함</td>
<td align="left"><code>np.sum(a)</code></td>
<td align="left"><code>21</code></td>
</tr>
<tr>
<td align="left"><code>np.mean()</code></td>
<td align="left">배열 원소들의 평균을 계산함</td>
<td align="left"><code>np.mean(a)</code></td>
<td align="left"><code>3.5</code></td>
</tr>
<tr>
<td align="left"><code>np.max()</code></td>
<td align="left">배열 원소 중 최댓값을 반환함</td>
<td align="left"><code>np.max(a)</code></td>
<td align="left"><code>6</code></td>
</tr>
<tr>
<td align="left"><code>np.min()</code></td>
<td align="left">배열 원소 중 최솟값을 반환함</td>
<td align="left"><code>np.min(a)</code></td>
<td align="left"><code>1</code></td>
</tr>
<tr>
<td align="left"><code>np.std()</code></td>
<td align="left">배열 원소들의 표준편차를 계산함</td>
<td align="left"><code>np.std(a)</code></td>
<td align="left">약 <code>1.7078</code></td>
</tr>
<tr>
<td align="left"><code>브로드캐스팅(자동)</code></td>
<td align="left">서로 다른 크기의 배열끼리도 자동으로 연산 맞춰줌</td>
<td align="left"><code>a + 1</code>, <code>a + [1,2,3]</code></td>
<td align="left">각 요소에 연산 적용</td>
</tr>
<tr>
<td align="left"><code>인덱싱/슬라이싱</code></td>
<td align="left">배열에서 특정 요소나 구간을 선택함</td>
<td align="left"><code>a[0,1]</code>, <code>a[:,1]</code></td>
<td align="left">특정 값, 열 추출</td>
</tr>
<tr>
<td align="left">---</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left"># 브로드캐스팅</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 넘파이 배열끼리 모양(Shape)이 다를 때, 자동으로 모양을 맞춰서 연산해 주는 기능</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">---</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left"># 브로드캐스팅 가능 조건</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 뒤에서부터 차원을 비교했을 때, 둘이 같거나 둘중 하나가 1이면 브로드캐스팅이 가능함</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 1인 쪽이 다른 쪽에 맞게 복제됨</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 두 차원이 같으면 그대로 사용함</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 다르고 둘 다 1이 아니면 에러 발생</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">---</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left"># 브로드캐스팅 예시</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">```python</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">import numpy as np</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">nd1 = np.arange(5)</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">nd2 = np.arange(5).reshape(5,1)</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">```</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<ul>
<li><code>nd1</code> -&gt; <code>[0, 1, 2, 3, 4]</code> : 1차원 배열(5,)</li>
<li><code>nd2</code> -&gt; <code>[[0], [1], [2], [3], [4]]</code> : 2차원 배열(1,5)</li>
<li><code>nd1 + nd2</code> ??</li>
</ul>
<h2 id="브로드캐스팅-과정">브로드캐스팅 과정</h2>
<ol>
<li><p>뒤에서부터 비교함 <code>1 vs 5</code></p>
</li>
<li><p><code>1</code>은 <strong>자동으로 복제</strong>되서 5로 변함(nd2 배열이 (5,5)로 변함</p>
<pre><code class="language-lua"> # 변한 nd2
 [[0, 0, 0, 0, 0],
  [1, 1, 1, 1, 1],
  [2, 2, 2, 2, 2],
  [3, 3, 3, 3, 3],
  [4, 4, 4, 4, 4]]</code></pre>
<ol start="3">
<li><p><code>nd2 + nd1</code> 수행 가능( (5, 5), (5,) )</p>
<pre><code class="language-lua">nd2: 
[[0, 0, 0, 0, 0],
[1, 1, 1, 1, 1],
[2, 2, 2, 2, 2],
[3, 3, 3, 3, 3],
[4, 4, 4, 4, 4]]

+
nd1: 
[0, 1, 2, 3, 4]

-&gt; 첫 행부터 차례대로 n1 n2를 더해서 결과 반환

결과:
[[0, 1, 2, 3, 4],
[1, 2, 3, 4, 5],
[2, 3, 4, 5, 6],
[3, 4, 5, 6, 7],
[4, 5, 6, 7, 8]]</code></pre>
</li>
</ol>
<hr />
<h1 id="axis">axis</h1>
<ul>
<li><code>axis= 0</code> 행 방향으로 계산</li>
<li><code>axis= 1</code> 열 방향으로 계산</li>
<li><code>axis= 2</code> 깂이 방향으로 계산</li>
</ul>
<hr />
<h1 id="행렬의-내적dot-product">행렬의 내적(dot product)</h1>
<ul>
<li>하나의 행렬의 행과 다른 행렬의 열을 곱하고 합쳐서 새로운 값을 만드는 것</li>
<li>원소별 곱 -&gt; 모두 더함</li>
</ul>
<hr />
</li>
</ol>
<h1 id="행렬-내적이-가능한-조건">행렬 내적이 가능한 조건</h1>
<ul>
<li>(앞 행렬의 열 개수) == (뒤 행렬의 행 개수) 여야 함</li>
<li>(m, n) × (n, p) -&gt; 결과는 (m, p) 모양!</li>
</ul>
<hr />
<h1 id="행렬-내적-예시">행렬 내적 예시</h1>
<pre><code class="language-python">import numpy as np

A = np.array([[1, 2],
              [3, 4]])

B = np.array([[5, 6],
              [7, 8]])

print(np.dot(A, B))</code></pre>
<ul>
<li>C[0, 0]:<ul>
<li>(1×5) + (2×7) = 5 + 14 = 19</li>
</ul>
</li>
<li>C[0, 1]:<ul>
<li>(1×6) + (2×8) = 6 + 16 = 22</li>
</ul>
</li>
<li>C[1, 0]:<ul>
<li>(3×5) + (4×7) = 15 + 28 = 43</li>
</ul>
</li>
<li>C[1, 1]:<ul>
<li>(3×6) + (4×8) = 18 + 32 = 50</li>
</ul>
</li>
<li>최종 결과<pre><code class="language-lua">[[19 22]
[43 50]]</code></pre>
<h1 id="내적-사용-코드">내적 사용 코드</h1>
<table>
<thead>
<tr>
<th align="left">코드</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>np.dot(A, B)</code></td>
<td align="left">행렬 A와 B의 내적</td>
</tr>
<tr>
<td align="left"><code>A @ B</code></td>
<td align="left">파이썬 3.5+에서는 <code>@</code> 기호도 가능</td>
</tr>
<tr>
<td align="left"><code>np.matmul(A, B)</code></td>
<td align="left">내적 전용 함수 (dot과 비슷)</td>
</tr>
</tbody></table>
</li>
</ul>
<hr />
<h1 id="외적cross-product">외적(cross product)</h1>
<ul>
<li>두 벡터로부터 새로운 &quot;벡터&quot;를 만드는 연산</li>
<li><strong>내적</strong>은 하나의 수(스칼라)를 만들고 <strong>외적</strong>은 &quot;새로운 벡터&quot;를 만듦</li>
<li>외적은 반드시 3차원 벡터끼리만 할 수 있음</li>
</ul>
<hr />
<h1 id="외적-계산-방법">외적 계산 방법</h1>
<pre><code class="language-ini">A = [a1, a2, a3]
B = [b1, b2, b3]</code></pre>
<ul>
<li>두 벡터 A와 B가 있을 때 외적 결과는<pre><code class="language-markdown">A × B = [a2*b3 - a3*b2,   a3*b1 - a1*b3,   a1*b2 - a2*b1]</code></pre>
</li>
</ul>
<hr />
<h1 id="npy-npz-파일-차이">npy, npz 파일 차이</h1>
<ul>
<li>npy: 하나의 넘파이 배열만 저장</li>
<li>npz: 여러 개 읨파이 배열을 묶어서 저장</li>
</ul>
<hr />
<h1 id="jpg-이미지를-불러왔을-때-나오는-numpy-배열">jpg 이미지를 불러왔을 때 나오는 numpy 배열</h1>
<pre><code class="language-ini">(720, 647, 3) [[[161 151 129]
  [189 179 157]
  [182 172 150]
  ...
  [109  94  86]
  [109  94  86]
  [110  96  87]]

 [[161 151 129]
  [189 179 157]
  [182 172 150]
  ...
  [103  89  80]
  [103  89  80]
  [104  90  81]]

 [[162 152 130]
  [190 180 158]
  [183 173 151]
  ...
  [102  87  79]
  [102  87  79]
  [103  89  80]]

 ...
...
  ...
  [115  82  63]
  [115  82  63]
  [115  82  63]]]</code></pre>
<h2 id="1-720-647-3">1. (720, 647, 3)</h2>
<ul>
<li>배열의 shape 모양</li>
<li>각각의 의미</li>
</ul>
<table>
<thead>
<tr>
<th align="left">번호</th>
<th align="left">의미</th>
</tr>
</thead>
<tbody><tr>
<td align="left">720</td>
<td align="left">세로(높이, height) 720픽셀</td>
</tr>
<tr>
<td align="left">647</td>
<td align="left">가로(너비, width) 647픽셀</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">채널(channel) 3개 (RGB: 빨강, 초록, 파랑)</td>
</tr>
<tr>
<td align="left">- 720 x 647 크기의 컬러(RGB) 이미지</td>
<td align="left"></td>
</tr>
</tbody></table>
<h2 id="2-안에-있는-데이터-구조">2. 안에 있는 데이터 구조</h2>
<pre><code class="language-ini">[161 151 129]
[189 179 157]
[182 172 150]
...</code></pre>
<ul>
<li>한 픽셀당 (R, G, B) 3개 값을 가진다는 뜻</li>
<li><code>[161 151 129]</code> -&gt; R: 161, G: 151, B: 129</li>
<li>0에 가까울수록 어두움, 255이면 밝음</li>
<li>데이터 타입은 <code>uint8</code>(부호 없는 8비트 정수)</li>
</ul>
<h2 id="3-추가">3. 추가</h2>
<ul>
<li>흑백 이미지는 2차원만 됨</li>
<li>OpenCV로 이미지를 읽을 때는 RGB가 아닌 BGR 순서로 되어 있음</li>
<li>투명도가 추가될 수 있음(RGB<strong>A</strong>)<ul>
<li>투명도: 이미지에서 픽셀이 얼마나 불투명하거나 투명한지를 나타내는 값(0~255), 0에 가까울수록 투명해짐</li>
</ul>
</li>
</ul>