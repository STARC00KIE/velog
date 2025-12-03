<h1 id="1-추론-및-논리-중심-reasoning-focused">1. 추론 및 논리 중심 (Reasoning-Focused)</h1>
<ul>
<li>단순히 문서를 검색해서 답을 찾는 것이 아니라, 검색된 정보를 바탕으로 논리적 연결을 해야 답을 할 수 있는 유형</li>
</ul>
<h2 id="multi-hop-다단계-추론">Multi-hop (다단계 추론)</h2>
<ul>
<li>정의: 하나의 문서나 문단에서 답을 찾을 수 없고, 서로 다른 위치에 있는 두 개 이상의 정보를 연결해야만 답을 도출할 수 있는 질문
&quot;&quot;&quot;
예시: &quot;A 제품의 배터리를 공급하는 회사의 본사는 어디에 위치해 있나요?&quot; (1. A 제품의 배터리 공급사 찾기 -&gt; 2. 그 회사의 본사 위치 찾기)
&quot;&quot;&quot;</li>
</ul>
<h2 id="comparative-비교-분석">Comparative (비교 분석)</h2>
<ul>
<li>정의: 두 개 이상의 대상(제품, 규정, 개념 등)에 대해 공통점이나 차이점을 묻는 질문</li>
<li>중요성: 모델이 여러 텍스트를 동시에 참조하여 분석하는 능력을 평가합니다.<pre><code>예시: &quot;취업규칙 제5조와 제12조에서 규정하는 휴가일수의 차이점은 무엇인가요?&quot;</code></pre></li>
</ul>
<h2 id="causal-인과-관계">Causal (인과 관계)</h2>
<ul>
<li>정의: 특정 현상의 '원인(Why)'이나 '결과(Effect)'를 묻는 질문, 텍스트 내에 명시된 인과관계를 파악해야 함<pre><code>예시: &quot;시스템 로그에서 'Timeout' 에러가 발생했을 때, 서버가 재부팅되는 이유는 무엇인가요?&quot;</code></pre></li>
</ul>
<h1 id="2-조건-및-제약-중심-constraint-based">2. 조건 및 제약 중심 (Constraint-Based)</h1>
<ul>
<li>특정 상황이나 조건이 주어졌을 때 모델이 올바르게 판단하는지 확인하는 유형</li>
</ul>
<h2 id="conditional-조건부-질문">Conditional (조건부 질문)</h2>
<ul>
<li>정의: &quot;만약 ~라면&quot;이라는 가정을 전제로 답을 요구하는 질문<pre><code>예시: &quot;재직 기간이 1년 미만인 직원이 퇴사할 경우, 퇴직금 산정 방식은 어떻게 되나요?&quot;</code></pre></li>
</ul>
<h2 id="temporal-시간순서-기반">Temporal (시간/순서 기반)</h2>
<ul>
<li>정의: 사건의 전후 관계나 특정 시점의 정보를 묻는 질문, Procedural(절차)과는 다르게 'When', 'After what'에 초점을 맞춤 <pre><code>예시: &quot;보안 패치를 설치하기 직전에 반드시 수행해야 할 작업은 무엇인가요?&quot;</code></pre></li>
</ul>
<h1 id="3-정보-종합-및-변환-synthesis--transformation">3. 정보 종합 및 변환 (Synthesis &amp; Transformation)</h1>
<ul>
<li>정보를 있는 그대로 가져오는 것이 아니라, 요약하거나 형태를 바꾼 질문</li>
</ul>
<h2 id="summarization-요약">Summarization (요약)</h2>
<p>정의: 긴 텍스트의 핵심 내용을 짧게 압축하여 설명하는 것을 요구하는 질문</p>
<pre><code>예시: &quot;이번 회의록에서 언급된 주요 결정 사항 3가지를 요약해 주세요.&quot;</code></pre><h2 id="extraction-정보-추출">Extraction (정보 추출)</h2>
<p>정의: 텍스트 내에서 특정 조건(날짜, 이름, 금액 등)에 맞는 엔티티(Entity)만을 뽑아내어 리스트화를 요구하는 질문</p>
<pre><code>예시: &quot;제공된 문서에서 언급된 모든 '협력업체 명'과 '계약 기간'을 표로 정리해 주세요.&quot;</code></pre>