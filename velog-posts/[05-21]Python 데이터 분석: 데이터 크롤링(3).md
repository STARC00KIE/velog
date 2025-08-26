<h1 id="selenium">Selenium</h1>
<ul>
<li>웹 브라우저를 사람처럼 자동으로 조작할 수 있게 해주는 웹 자동화 도구</li>
</ul>
<hr />
<h1 id="selenium-사용-이유">Selenium 사용 이유</h1>
<table>
<thead>
<tr>
<th>상황</th>
<th>이유</th>
</tr>
</thead>
<tbody><tr>
<td><strong>JavaScript로 렌더링된 웹사이트</strong></td>
<td><code>requests</code>나 <code>BeautifulSoup</code>으로는 내용이 안 보임</td>
</tr>
<tr>
<td><strong>버튼 클릭 후 데이터 로드되는 구조</strong></td>
<td>버튼 클릭/스크롤/탭 전환 등 사용자 동작 필요</td>
</tr>
<tr>
<td><strong>로그인이 필요한 페이지</strong></td>
<td>로그인 폼 자동 입력 + 제출 가능</td>
</tr>
<tr>
<td><strong>웹 테스트 자동화</strong></td>
<td>QA(품질관리)에서 자동 테스트에 활용</td>
</tr>
</tbody></table>
<hr />
<h1 id="selenium-명령어">Selenium 명령어</h1>
<table>
<thead>
<tr>
<th>명령</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><code>driver.get(URL)</code></td>
<td>해당 웹페이지 열기</td>
</tr>
<tr>
<td><code>find_element(By.ID/CLASS_NAME/NAME/XPATH)</code></td>
<td>HTML 요소 하나 찾기</td>
</tr>
<tr>
<td><code>element.click()</code></td>
<td>클릭</td>
</tr>
<tr>
<td><code>element.send_keys('텍스트')</code></td>
<td>텍스트 입력</td>
</tr>
<tr>
<td><code>driver.quit()</code></td>
<td>브라우저 종료</td>
</tr>
</tbody></table>
<hr />
<h1 id="id-선택자"><code>ID</code> 선택자</h1>
<ul>
<li>HTML 요소의 id 속성값을 이용해 정확하게 하나의 요소를 찾는 방법</li>
<li>빠르고 가장 안정적</li>
<li><code>&lt;input id=&quot;search&quot; type=&quot;text&quot;&gt;</code> 일 때</li>
<li><code>element = driver.find_element(By.ID, 'search')</code> 로 찾으면 됨</li>
</ul>
<hr />
<h1 id="xpath-선택자"><code>XPath</code> 선택자</h1>
<ul>
<li>HTML 문서의 노드 경로를 기반으로 요소를 탐색함.</li>
<li>복잡한 구조에서도 원하는 요소를 정확하게 찾을 수 있음.</li>
<li>텍스트 포함, 속성 조건, 위치 기반 등 유연한 조건 설정 가능.<pre><code class="language-html">&lt;div class=&quot;wrapper&quot;&gt;
&lt;input type=&quot;text&quot; name=&quot;email&quot; /&gt;
&lt;/div&gt;</code></pre>
<pre><code class="language-python"># 다음과 같이 찾으면 됨
# 절대 경로
element = driver.find_element(By.XPATH, '/html/body/div/input')
# 속성 기반
element = driver.find_element(By.XPATH, '//input[@name=&quot;email&quot;]')
# 텍스트 기반
element = driver.find_element(By.XPATH, '//button[text()=&quot;로그인&quot;]')</code></pre>
</li>
</ul>
<hr />
<h1 id="css-selector-선택자"><code>CSS Selector</code> 선택자</h1>
<ul>
<li>CSS 스타일 정의에 쓰는 문법을 이용해 요소를 선택함</li>
<li>클래스, ID, 태그, 자식 관계 등 다양한 조합으로 탐색 가능함</li>
<li>짧고 빠르며 XPath보다 가독성 좋음 (하지만 텍스트 매칭은 XPath만 가능)<pre><code class="language-html">&lt;div class=&quot;box&quot;&gt;
&lt;input class=&quot;search-input&quot; /&gt;
&lt;/div&gt;</code></pre>
<pre><code class="language-python"># 다음과 같이 찾으면 됨
# 클래스 이름으로 선택
element = driver.find_element(By.CSS_SELECTOR, '.search-input')
# 태그 + 클래스 조합
element = driver.find_element(By.CSS_SELECTOR, 'div.box input')
# ID 선택
element = driver.find_element(By.CSS_SELECTOR, '#search')</code></pre>
</li>
</ul>
<hr />
<h1 id="css-selector-xpath-id">CSS Selector, XPath, ID</h1>
<table>
<thead>
<tr>
<th>기준</th>
<th>ID</th>
<th>XPath</th>
<th>CSS Selector</th>
</tr>
</thead>
<tbody><tr>
<td><strong>속도</strong></td>
<td>매우 빠름</td>
<td>느릴 수 있음</td>
<td>빠름</td>
</tr>
<tr>
<td><strong>가독성</strong></td>
<td>매우 좋음</td>
<td>복잡함</td>
<td>간결함</td>
</tr>
<tr>
<td><strong>유연성</strong></td>
<td>낮음</td>
<td>가장 유연함</td>
<td>중간 정도</td>
</tr>
<tr>
<td><strong>지원 기능</strong></td>
<td>단일 속성만</td>
<td>텍스트 탐색, 조건 검색</td>
<td>계층 구조, 클래스 조합</td>
</tr>
<tr>
<td><strong>추천 사용처</strong></td>
<td>ID가 있을 때</td>
<td>복잡한 구조, 텍스트 기반</td>
<td>대부분의 상황에서 적합</td>
</tr>
</tbody></table>