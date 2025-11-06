<h1 id="1-vlm-ocr-모델별-사용한-벤치마크hf-참고">1. VLM-OCR 모델별 사용한 벤치마크(HF 참고)</h1>
<h2 id="a-deepseek-ocr">a. DeepSeek-OCR</h2>
<ul>
<li>Fox</li>
<li>OmniDocBench</li>
</ul>
<h2 id="b-paddleocr-vl">b. PaddleOCR-VL</h2>
<ul>
<li>OmniDocBench</li>
</ul>
<h2 id="c-dotsocr">c. dots.ocr</h2>
<ul>
<li>olmOCR-bench</li>
<li>OmniDocBench</li>
<li>dots.ocr-bench</li>
</ul>
<h2 id="d-chandra">d. Chandra</h2>
<ul>
<li>olmOCR-bench</li>
</ul>
<h2 id="e-lightonocr">e. LightOnOCR</h2>
<ul>
<li>Olmo-Bench</li>
</ul>
<h2 id="f-nemo-retriever-ocr-v1">f. NeMo Retriever OCR v1</h2>
<ul>
<li>자체 벤치마크</li>
</ul>
<h2 id="g-olmocr">g. OlmOCR</h2>
<ul>
<li>olmOCR-bench</li>
</ul>
<hr />
<h1 id="2-olmocr-bench">2. olmOCR-bench</h1>
<h2 id="a-개요">a. 개요</h2>
<ul>
<li>PDF -&gt; Markdown 변환을 수행하는 OCR/문서이해 시스템이 텍스트와 문서 구조를 얼마나 잘 보존하는지 Unit Test로 자동 평가하는 벤치마크</li>
<li>총 1403개의 PDF가 포함되어 있고 각 PDF/페이지에 대해 다섯 가지 관점으로 정밀 점검을 진행함<h2 id="b-정밀-점검을-위한-5가지-관점">b. 정밀 점검을 위한 5가지 관점</h2>
</li>
<li>Text Presence(텍스트 존재 여부)<ul>
<li>지정한 짧은 문장(1-3문장)이 결과에 있어야 하는지 확인</li>
</ul>
</li>
<li>Text Absence(텍스트 부재 여부)<ul>
<li>머리글, 꼬리글, 페이지 번호 등 없어야 하는 텍스트가 제거되었는지 확인</li>
</ul>
</li>
<li>Natural Reading Order(자연스러운 읽기 순서)<ul>
<li>두 텍스트 구간의 상대 순서가 자연스러운지 확인</li>
</ul>
</li>
<li>Table Accuracy(표 인식 정확도)<ul>
<li>표 및 셀의 값이 이웃 관계까지 맞는지 확인(Markdown, HTML 모두 허용)</li>
</ul>
</li>
<li>Math Formula Accuracy(수식 인식 정확도)<ul>
<li>수식의 기호 배치/상대 위치를 본떠 탐지</li>
</ul>
</li>
</ul>
<h2 id="c-평가에-사용된-ocr-도구">c. 평가에 사용된 OCR 도구</h2>
<h3 id="olmlcrbench-폴더-내부에-스크립트-존재">olmlcr/bench 폴더 내부에 스크립트 존재</h3>
<ul>
<li>OlmOCR1, 2</li>
<li>paddleOCRVL</li>
<li>PPStructureV3</li>
<li>Nanonets-OCR</li>
<li>Mistral</li>
<li>mineru</li>
<li>marker</li>
<li>got ocr</li>
<li>gemini-2</li>
<li>docling</li>
<li>claude-3.7-sonnet</li>
<li>chatgpt-4o</li>
</ul>
<h2 id="d-데이터-구조">d. 데이터 구조</h2>
<pre><code class="language-text">data_folder/
├── pdfs/              # 평가할 PDF 파일들
│   ├── doc1.pdf
│   └── doc2.pdf
├── *.jsonl            # 테스트 정의 파일들 (multi_column.jsonl, math.jsonl 등)
└── candidate_folders/ # OCR 도구별 출력 폴더
    ├── olmocr/
    │   ├── doc1_pg1_repeat1.md
    │   ├── doc1_pg1_repeat2.md
    │   └── ...
    ├── marker/
    └── mineru/</code></pre>
<h2 id="e-전체-파이프라인-요약">e. 전체 파이프라인 요약</h2>
<pre><code class="language-text">준비:   PDF → 마크다운 변환 (별도 실행, --repeats 3)
  ↓
입력:   변환된 MD 파일들 + 테스트 정의 (*.jsonl)
  ↓
1단계:  각 테스트를 모든 파일들에 실행(반복적으로 생성한 파일 포함)
  ↓
2단계:  반복 결과들 중에서 50% 이상 통과 시 성공 판정
  ↓
3단계:  JSONL 파일별 통과율 계산 후 평균
  ↓
4단계:  부트스트랩으로 신뢰구간 계산
  ↓
출력:   OCR 도구별 점수, 신뢰구간, 카테고리별 분석</code></pre>
<hr />
<h1 id="3-테스트-타입">3. 테스트 타입</h1>
<h2 id="a-테스트-타입별-평가-방식">a. 테스트 타입별 평가 방식</h2>
<table>
<thead>
<tr>
<th>테스트 종류</th>
<th>목적</th>
<th>예시</th>
</tr>
</thead>
<tbody><tr>
<td>Present</td>
<td>특정 텍스트가 올바르게 인식되었는지 확인</td>
<td><code>&quot;Figure 1&quot;</code>이 마크다운에 존재하는가?</td>
</tr>
<tr>
<td>Absent</td>
<td>불필요한 텍스트가 없는지 확인</td>
<td>워터마크가 텍스트로 인식되지 않았는가?</td>
</tr>
<tr>
<td>Order</td>
<td>텍스트 순서가 올바른지 확인</td>
<td>제목이 본문보다 먼저 나오는가?</td>
</tr>
<tr>
<td>Table</td>
<td>표 구조가 올바르게 변환되었는지 확인</td>
<td>행/열 개수가 맞는가?</td>
</tr>
<tr>
<td>Math</td>
<td>수식이 정확하게 인식되었는지 확인</td>
<td>LaTeX 수식이 올바른가?</td>
</tr>
<tr>
<td>Baseline</td>
<td>기본적인 텍스트 존재 확인</td>
<td>페이지가 비어있지 않은가?</td>
</tr>
</tbody></table>
<h2 id="b-테스트-타입별-상세">b. 테스트 타입별 상세</h2>
<h3 id="--fuzzy">- fuzzy</h3>
<ul>
<li>이분법에 의해 확연히 구분되는 전통적인 논리가 아닌, 특정 모호한 놀리가 그 집합에 어느정도 속하는지를 표헌하는 방법</li>
</ul>
<hr />
<ul>
<li><p>고전적 집합 (특성함수: $f(x)$
$$
f(x)=
\begin{cases}
1,,x\in A,;x가,A에,포함된다. \
0,,x\notin,A,;x가,A에,포함되지,않는다.
\end{cases}
$$</p>
</li>
<li><p>퍼지 집합 (소속함수: $\mu(x)$)
$$
\mu(x)=
\begin{cases}
\mu_A(x)=1,;x가,A에,속한다.\
\mu_A(x)=0,;x가,A에,속하지,않는다.\
0&lt;\mu_A(x)&lt;1,;x가,A에,부분적으로,속한다.\
\end{cases}
$$</p>
</li>
</ul>
<hr />
<ul>
<li>파이썬에서 문자열 간 유사도를 계산하는 모듈</li>
<li>0-100(0.0-1.0) 범위의 유사도 점수를 반환함</li>
<li>주로 사용되는 지표<ul>
<li><code>ratio(a,b)</code><ul>
<li>두 문자열 전체를 정확히 1:1로 비교</li>
<li>두 문구가 거의 그대로여야 할 때 사용함</li>
</ul>
</li>
<li><code>partial_ratio(a,b)</code><ul>
<li>a가 b의 일부 구간과 얼마나 비슷한지 측정함</li>
<li>긴 본문에서 캡션이나 제목 같은 연속된 구간을 찾는 데 유용함</li>
</ul>
</li>
<li><code>token_sort_ratio(a,b)</code><ul>
<li>단어(토큰) 정렬 후 비교, 단어 순서가 달라도 문자열이 유사하면 높은 점수 부여</li>
</ul>
</li>
<li><code>token_set_ratio(a,b)</code><ul>
<li>두 문자열의 공통 단어 집합 위주로 비교, 중복되거나 불필요한 토큰(중복, 수식어)이 많을 때 사용함</li>
</ul>
</li>
</ul>
</li>
</ul>
<hr />
<h3 id="--text-presence-test-present--absent">- Text Presence Test (present / absent)</h3>
<ul>
<li>Threshold 계산<ul>
<li><code>threshold = 1.0 - (max_diffs / text_length)</code></li>
<li><code>max_diffs</code>: 기준 문자열에서 허용할 &quot;다른 문자 수&quot;의 상한을 의미함</li>
<li><code>text_length</code>: 기준으로 설정한 문자열 길이</li>
<li>예: max_diffs=2, text_length=10 → threshold = 0.8</li>
</ul>
</li>
<li>Fuzzy 매칭: <ul>
<li><code>best_ratio = fuzz.partial_ratio(reference_query, md_content) / 100.0</code> 로 기준 문자열이 본문의 어떤 연속 구간과 얼마나 비슷한가를 측정하여 최고 유사도를 반환함</li>
</ul>
</li>
<li>판정 로직<ul>
<li>present: best_ratio &gt;= threshold → 통과</li>
<li>absent: best_ratio &lt; threshold → 통과</li>
</ul>
</li>
</ul>
<h3 id="--text-order-test">- Text Order Test</h3>
<ul>
<li><p>fuzzy 매칭으로 위치 후보 찾기</p>
<ul>
<li><code>find_near_matches(self.before, md_content, max_l_dist=self.max_diffs)</code></li>
<li><code>find_near_matches(self.after, md_content, max_l_dist=self.max_diffs)</code></li>
<li>둘 중 하나라도 비어 있으면 즉시 실패 판정</li>
</ul>
</li>
<li><p>순서 판정</p>
<pre><code class="language-python"># test.py(602-617)
# n*m
for before_match in before_matches:
for after_match in after_matches:
if before_match.start &lt; after_match.start: return True</code></pre>
</li>
<li><p>하나라도 <code>before</code>의 시작 인덱스가 <code>after</code>의 시작 인덱스보다 작으면 통과</p>
</li>
<li><p>모든 조합을 확인했는데도 <code>before.start &lt; after.start</code>가 한 번도 없으면 실패</p>
</li>
</ul>
<h3 id="--table-test">- Table Test</h3>
<ul>
<li>테이블 파싱<ul>
<li>Markdown.HTML 테이블을 파싱해 2차원 배열로 변환</li>
</ul>
</li>
<li>타깃 셀 후보 찾기<ul>
<li><code>fuzz.ratio</code>로 모든 셀 텍스트로 유사도 구하기</li>
<li>사전 정의된 threshold(철자 오차 허용 한도)를 넘는 셀들을 타깃 후보로 선정</li>
</ul>
</li>
<li>각각의 타깃 후보들을 요청에 포함된 조건에 부합하는지 검사<ul>
<li>left/right/up/down:<ul>
<li>타깃 셀과 인접한 셀 을 요청에 적힌 문자열과 비교(fuzz.ratio)</li>
<li>임계값 이상이면 일치로 판정</li>
</ul>
</li>
<li>top_heading(윗머리글)<ul>
<li>타깃 셀 기준 제일 위에 있는 셀 비교(fuzz.ratio)</li>
<li>임계값 이상이면 일치로 판정</li>
</ul>
</li>
<li>left_heading(왼쪽 머리글)<ul>
<li>타깃 셀 기중 제일 왼쪽에 있는 셀 비교(fuzz.ratio)</li>
<li>임계값 이상이면 일치로 판정</li>
</ul>
</li>
</ul>
</li>
<li>타깃 후보 중 하나라도 제공된 모든 조건이 각각 threshold를 넘으면 통과</li>
</ul>
<h3 id="--math-test">- Math Test</h3>
<ul>
<li><code>LaTex</code> 수식 추출<ul>
<li>찾은 수식들을 <code>equation</code>리스트에 저장</li>
</ul>
</li>
<li>요청한 수식과 같은 수식이 <code>equation</code>안에 존재할 때 <ul>
<li>즉시 통과</li>
</ul>
</li>
<li>존재하지 않을 때<ul>
<li><code>fuzz.ratio</code>로 유사도 내림차순 정렬(렌더링 비용 감소 최적화 위함)</li>
<li>후보 수식을 <code>KaTex</code>로 이미지 렌더링한 후, 렌더링된 요청 수식과 비교</li>
<li>(<code>Latex</code>보다 속도 빠르고, 같은 입력이면 항상 같은 출력이 나오기 때문에 <code>KaTex</code>로 변환)</li>
<li>동일하다고 판단되면 통과</li>
</ul>
</li>
</ul>
<h3 id="--baseline-test">- Baseline Test</h3>
<ul>
<li><strong>거의 빈 페이지여야 한다</strong>를 확인하는 용도의 테스트</li>
<li>빈 페이지 여부 검사<ul>
<li>텍스트에서 알파넘(alphabet + num) 문자만 모아 길이 계산</li>
<li><code>base_content_len &gt; max_length</code>면 실패</li>
<li><code>max_length</code>는 <code>JSONL</code>파일에 각각 적혀져 있음</li>
<li>성공하면 다른 검사들 즉시 통과</li>
</ul>
</li>
<li>알파넘 존재 확인(<code>max_length</code> 없을 때)<ul>
<li>문자 아예 없으면 실패</li>
</ul>
</li>
<li>텍스트 마지막 부분 반복 패턴 검사(품질 저하 탐지)<ul>
<li>모델이 같은 구문을 꼬리에 계속 복붙하는 루프를 잡아내기 위한 검사 </li>
</ul>
</li>
<li>금지 문자 검사(<code>check_disallowed_characters=True</code>일 때만 검사)<ul>
<li><code>CJK 한자(중국어), 히라가나/가타카나, 이모지(여러 블록), 국기 이모지</code>가 포함되면 실패</li>
<li>다국어/이모지 허용하지 않는 출력 규격을 강제할 때 유용함</li>
</ul>
</li>
</ul>
<hr />
<h1 id="4-총-검사">4. 총 검사</h1>
<ul>
<li><code>JSONL</code>파일 단위(카테고리/세트) 별로 그룹화 진행</li>
<li>각 <code>JSONL</code>파일별 통과율 계산<ul>
<li><code>pass_rate = passed / total</code> </li>
<li><code>total</code>: <code>JSONL</code>에서 나온 전체 테스트 수</li>
<li><code>passed</code>: 통과한 테스트 수</li>
<li><code>scores</code>: 각 테스트의 결과 점수(통과=1.0, 실패=0.0)</li>
</ul>
</li>
<li>통과율들의 산술 평균을 취해 <code>per_category_score</code>를 출력</li>
</ul>
<hr />
<h1 id="5-jsonl-파일">5. <code>JSONL</code> 파일</h1>
<h2 id="a-요약">a. 요약</h2>
<ul>
<li>`bench/miners 스크립트에서 특정 테스트 타입의 JSONL 파일을 생성하거나 수동으로 생성함</li>
<li>각각의 테스트 타입별로 별도의 파일 생성(math_tests.jsonl, table_tests.jsonl 등)</li>
<li><code>test.py</code>의 <code>save_tests()</code>함수를 이용하여 테스트 저장<h2 id="b-주요-마이닝-스크립트-요약-표">b. 주요 마이닝 스크립트 요약 표</h2>
<table>
<thead>
<tr>
<th>스크립트</th>
<th>생성 테스트 타입</th>
<th>방법</th>
</tr>
</thead>
<tbody><tr>
<td><code>mine_math.py</code></td>
<td>math</td>
<td>TeX 파일에서 수식 추출, KaTeX 검증</td>
</tr>
<tr>
<td><code>mine_tables_gpt.py</code></td>
<td>table</td>
<td>GPT-4o로 테이블 감지 및 관계 추출</td>
</tr>
<tr>
<td><code>mine_multi_column.py</code></td>
<td>order</td>
<td>Claude로 HTML 변환, 순서 추출</td>
</tr>
<tr>
<td><code>mine_old_scans.py</code></td>
<td>present, order</td>
<td>원본 텍스트에서 랜덤 세그먼트 추출</td>
</tr>
<tr>
<td><code>mine_headers_footers.py</code></td>
<td>absent</td>
<td>헤더/푸터 영역 감지, 부재 확인</td>
</tr>
<tr>
<td><code>mine_blank_pages_gpt.py</code></td>
<td>baseline</td>
<td>빈 페이지 검사 생성</td>
</tr>
<tr>
<td><code>mine_long_tiny_text.py</code></td>
<td>present</td>
<td>작은 글자 텍스트 추출</td>
</tr>
<tr>
<td>## c. <code>JSONL</code>파일 예시</td>
<td></td>
<td></td>
</tr>
<tr>
<td>```JSON</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;multi_column_miss.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;multi_column_miss_00&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;present&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;text&quot;: &quot;Corporate social responsibility and the tobacco industry: hope or hype?&quot;</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;multi_column_miss.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;multi_column_miss_01&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;present&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;text&quot;: &quot;this leaves BAT to argue why it should not be held to be largely accountable for the annual deaths of some 754 600 smokers, and Philip Morris some 803 600 smokers.&quot;</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;multi_column_miss.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;multi_column_miss_02&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;present&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;text&quot;: &quot;The term &quot;corporate social responsibility&quot; is in vogue at the moment but as a concept it is vague and means different things to different people.&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;max_diffs&quot;: 2</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;multi_column_miss.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;multi_column_miss_04&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;absent&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;text&quot;: &quot;Downloaded from <a href="http://tobaccocontrol.bmj.com/&quot;">http://tobaccocontrol.bmj.com/&quot;</a></td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;multi_column_miss.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;multi_column_miss_10&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;order&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;before&quot;: &quot;Corporate social responsibility and the tobacco industry: hope or hype?&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;after&quot;: &quot;The unprecedented expansion of power and influence of TNCs over the past three decades has accelerated global trade and development, but also environmental damage and abuses of&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;max_diffs&quot;: 2</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;olmo2-pg4.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;olmo2-pg4_table00&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;table&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;cell&quot;: &quot;Type&quot;</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;olmo2-pg4.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;olmo2-pg4_table01&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;table&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;cell&quot;: &quot;3.32T&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;left&quot;: &quot;3.71T&quot;</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;mathfuncs.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;mathfuncs_03&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;math&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;math&quot;: &quot;e^{i \pi}+1=0&quot;</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>{</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;pdf&quot;: &quot;blank_book_pg1.pdf&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;page&quot;: 1,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;id&quot;: &quot;test1_blank&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;type&quot;: &quot;baseline&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;checked&quot;: &quot;verified&quot;,</td>
<td></td>
<td></td>
</tr>
<tr>
<td>&quot;max_length&quot;: 10</td>
<td></td>
<td></td>
</tr>
<tr>
<td>}</td>
<td></td>
<td></td>
</tr>
<tr>
<td>```</td>
<td></td>
<td></td>
</tr>
</tbody></table>
</li>
</ul>