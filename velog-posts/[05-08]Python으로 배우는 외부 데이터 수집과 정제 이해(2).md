<h1 id="pandas">pandas</h1>
<ul>
<li>&quot;표 형식(테이블 형식)&quot; 데이터를 다루는 파이썬 라이브러리</li>
<li>엑셀처럼 행과 열이 있는 데이터</li>
<li>SQL처럼 테이블 같은 데이터</li>
<li>넘파이처럼 수치 연산도 가능한 데이터</li>
</ul>
<hr />
<h1 id="pandas의-핵심-자료구조">pandas의 핵심 자료구조</h1>
<table>
<thead>
<tr>
<th align="left">자료구조</th>
<th align="left">설명</th>
<th align="left">예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left">Series</td>
<td align="left">1차원 데이터 (리스트/배열 같은 것)</td>
<td align="left"><code>[10, 20, 30]</code></td>
</tr>
<tr>
<td align="left">DataFrame</td>
<td align="left">2차원 데이터 (표/엑셀 같은 것)</td>
<td align="left">(행과 열이 있는 표)</td>
</tr>
</tbody></table>
<hr />
<h1 id="pandas로-프로젝트를-진행할-때의-흐름">pandas로 프로젝트를 진행할 때의 흐름</h1>
<ol>
<li>파일(CSV, Excel 등) 읽기</li>
<li>데이터프레임 만들기</li>
<li>필요에 따라 데이터 가공 (정렬, 필터, 그룹핑 등)</li>
<li>분석/시각화</li>
<li>다시 파일로 저장</li>
</ol>
<hr />
<h1 id="메타데이터">메타데이터</h1>
<ul>
<li>본문 데이터는 아니지만, 그 데이터를 이해하는 데 필요한 부가 정보를 담고 있는 데이터</li>
<li>예시)<ul>
<li>사진 → 사진 자체는 이미지 데이터고, 메타데이터는 촬영 날짜, 해상도, 카메라 모델</li>
<li>파일 → 파일 이름, 크기, 생성일, 수정일</li>
<li>이미지 → 높이, 너비, 채널 수, 포맷, EXIF 정보 등</li>
</ul>
</li>
</ul>
<hr />
<h1 id="jsonjavascript-object-notation">JSON(JavaScript Object Notation)</h1>
<ul>
<li>데이터를 키(key)-값(value) 쌍으로 저장하는 가벼운 데이터 포맷</li>
<li>메타데이터를 JSON 형태로 저장하면  데이터에 대한 정보를 키-값 형태로 정리한 파일이 됨</li>
<li>예시<pre><code class="language-json">{
&quot;name&quot;: &quot;example.jpg&quot;,
&quot;height&quot;: 720,
&quot;width&quot;: 647,
&quot;channels&quot;: 3,
&quot;format&quot;: &quot;JPEG&quot;,
&quot;created&quot;: &quot;2024-05-01T12:00:00Z&quot;
}</code></pre>
</li>
</ul>
<hr />
<h1 id="메타데이터와-json이-자주-쓰이는-분야">메타데이터와 JSON이 자주 쓰이는 분야</h1>
<table>
<thead>
<tr>
<th align="left">분야</th>
<th align="left">사용 예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left">머신러닝 데이터셋</td>
<td align="left">이미지/라벨/크기 정보 저장</td>
</tr>
<tr>
<td align="left">디지털 자산 관리</td>
<td align="left">사진, 비디오, 오디오 파일의 부가정보 관리</td>
</tr>
<tr>
<td align="left">웹 개발</td>
<td align="left">API 응답에 메타데이터 포함 (ex: 페이지 수, 항목 수)</td>
</tr>
<tr>
<td align="left">클라우드 스토리지</td>
<td align="left">파일 업로드할 때 파일 메타데이터 저장</td>
</tr>
</tbody></table>
<hr />
<h1 id="glob">glob</h1>
<ul>
<li>파일 시스템 안에서 <strong>특정 패턴</strong>에 맞는 파일 목록을 찾아주는 모듈</li>
<li>폴더 안에 조건에 맞는 파일만 찾아서 가져올 수 있음<pre><code class="language-python">import glob
</code></pre>
</li>
</ul>
<h1 id="특정-폴더-안-파일-찾기">특정 폴더 안 파일 찾기</h1>
<p>file_list = glob.glob('폴더경로/*.txt')</p>
<p>for file in file_list:
    print(file)</p>
<p>```</p>
<ul>
<li><code>glob.glob('폴더/*.txt')</code> → 폴더 안의 <code>.txt</code> 파일만 찾기</li>
<li>결과는 <strong>파일 경로 리스트</strong>로 반환됨</li>
</ul>
<hr />
<h1 id="if-__name__--__main__"><code>if __name__ == &quot;__main__&quot;:</code></h1>
<ul>
<li>이 파일을 &quot;직접 실행&quot;할 때만 실행되게 하는 문법이야.</li>
<li>다른 곳에서 파일을 가져다 쓸땐 실행되지 않음</li>
<li>파일을 직접 실행했을 때 
<code>python a.py</code> -&gt; <code>if __name__ == &quot;__main__&quot;:</code> 내부가 실행됨</li>
<li><code>import a</code> -&gt; 다른 파일에서 a 를 불러오먄 <code>if __name__ == &quot;__main__&quot;:</code> 내부 실행되지 않음</li>
<li>굳이 쓸 필요 없지만 지금부터 쓰는 습관 들이기</li>
</ul>