<h1 id="데이터-분석-5단계">데이터 분석 5단계</h1>
<h2 id="질문---수집-정리---탐색---결론---공유">질문 -&gt; 수집, 정리 -&gt; 탐색 -&gt; 결론 -&gt; 공유</h2>
<table>
<thead>
<tr>
<th align="left">단계</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>1. 질문하기 (Ask questions)</strong></td>
<td align="left">- 분석의 출발점. 어떤 문제를 해결하고 싶은가?<br /> - 질문이 먼저일 수도, 데이터를 보고 질문을 만들 수도 있음.</td>
</tr>
<tr>
<td align="left"><strong>2. 데이터 랭글링 (Wrangle data)</strong></td>
<td align="left">- 데이터를 수집(gather), 평가(assess), 정제(clean)하는 과정.<br /> - 분석 가능한 형태로 가공하는 단계.</td>
</tr>
<tr>
<td align="left"><strong>3. 데이터 탐색 (Exploratory Data Analysis, EDA)</strong></td>
<td align="left">- 통계, 시각화 등을 통해 데이터의 패턴과 관계 파악.<br /> - 통찰(insight)을 얻고, 직관을 극대화하는 핵심 단계.</td>
</tr>
<tr>
<td align="left"><strong>4. 결론 도출 또는 예측 (Draw conclusions or make predictions)</strong></td>
<td align="left">- 분석 내용을 바탕으로 결론 도출 또는 예측 수행.<br /> - 머신러닝 모델 적용도 이 단계에 포함.</td>
</tr>
<tr>
<td align="left"><strong>5. 결과 공유 (Communicate the results)</strong></td>
<td align="left">- 보고서, 블로그, 발표 등 다양한 방식으로 결과 전달.<br /> - 이해관계자와 인사이트를 효과적으로 공유.</td>
</tr>
</tbody></table>
<hr />
<h1 id="seaborn">Seaborn</h1>
<ul>
<li><strong>matplotlib</strong> 위에서 작동하는 Python의 시각화 라이브러리</li>
<li>데이터프레임과 통계적 시각화에 최적화되어 있음</li>
</ul>
<hr />
<h1 id="seaborn의-주요-특징">seaborn의 주요 특징</h1>
<table>
<thead>
<tr>
<th align="left">특징</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>Pandas 친화적</strong></td>
<td align="left"><code>DataFrame</code>을 바로 넘겨서 컬럼 이름으로 시각화 가능</td>
</tr>
<tr>
<td align="left"><strong>matplotlib보다 간결한 문법</strong></td>
<td align="left">코드가 짧고 예쁘게 나옴</td>
</tr>
<tr>
<td align="left"><strong>자동 통계 계산</strong></td>
<td align="left">평균, 신뢰구간(CI) 등 자동 집계</td>
</tr>
<tr>
<td align="left"><strong>고급 스타일 내장</strong></td>
<td align="left">기본 색상, 스타일이 깔끔하고 모던함</td>
</tr>
<tr>
<td align="left"><strong>matplotlib 기반</strong></td>
<td align="left">필요하면 <code>plt</code>와 같이 사용 가능</td>
</tr>
</tbody></table>
<hr />
<h1 id="기본-사용-예시">기본 사용 예시</h1>
<pre><code class="language-python">import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

tips = sns.load_dataset(&quot;tips&quot;)  # 내장 예제 데이터셋

sns.barplot(x=&quot;day&quot;, y=&quot;total_bill&quot;, data=tips)
plt.title(&quot;요일별 평균 식사 금액&quot;)
plt.show()</code></pre>
<hr />
<h1 id="seaborn-자주-쓰는-함수들">seaborn 자주 쓰는 함수들</h1>
<table>
<thead>
<tr>
<th align="left">함수</th>
<th align="left">그래프 종류</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>sns.barplot()</code></td>
<td align="left">막대그래프</td>
<td align="left">평균 + 신뢰구간 표시</td>
</tr>
<tr>
<td align="left"><code>sns.countplot()</code></td>
<td align="left">빈도 막대그래프</td>
<td align="left">값 개수 세기</td>
</tr>
<tr>
<td align="left"><code>sns.lineplot()</code></td>
<td align="left">선 그래프</td>
<td align="left">시간 추세, 선형성 확인</td>
</tr>
<tr>
<td align="left"><code>sns.boxplot()</code></td>
<td align="left">박스플롯</td>
<td align="left">이상치 탐지 및 분포 확인</td>
</tr>
<tr>
<td align="left"><code>sns.violinplot()</code></td>
<td align="left">분포 + 밀도 혼합 그래프</td>
<td align="left"></td>
</tr>
<tr>
<td align="left"><code>sns.histplot()</code></td>
<td align="left">히스토그램</td>
<td align="left"></td>
</tr>
<tr>
<td align="left"><code>sns.kdeplot()</code></td>
<td align="left">밀도 곡선 (부드러운 분포)</td>
<td align="left"></td>
</tr>
<tr>
<td align="left"><code>sns.scatterplot()</code></td>
<td align="left">산점도</td>
<td align="left"></td>
</tr>
<tr>
<td align="left"><code>sns.heatmap()</code></td>
<td align="left">상관관계 등 2D 행렬 시각화</td>
<td align="left"></td>
</tr>
<tr>
<td align="left"><code>sns.pairplot()</code></td>
<td align="left">수치형 변수 쌍 전체를 비교 (자동 그리드)</td>
<td align="left"></td>
</tr>
</tbody></table>
<hr />
<h1 id="기술-통계-변랑과-데이터-정의">기술 통계, 변랑과 데이터 정의</h1>
<ul>
<li>기술 통계: 수집한 데이터를 수치나 표, 그래프 등으로 정리하여 데이터 전체가 나타내는 경향이나 성질을 파악하는 방법</li>
<li>변량: 어떤 집단을 구성하는 물건의 특성을 수치로 표현한 값</li>
<li>데이터: 조사나 실험 등으로 얻은 변량의 관측값이나 측정값을 모은 것, 데이터가 흗어진 분포를 나타내기 위한 값들로는 대표값, 상자수염도, 분산, 표준편차 등이 있음</li>
</ul>
<hr />
<h1 id="질적-양적데이터-정리">질적, 양적데이터 정리</h1>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left">하위 유형</th>
<th align="left">설명</th>
<th align="left">예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>질적 데이터</strong> (Qualitative / 범주형)</td>
<td align="left">명목형 (Nominal)</td>
<td align="left">순서 없음, 단순 분류</td>
<td align="left">성별, 혈액형, 도시명, 색깔</td>
</tr>
<tr>
<td align="left"></td>
<td align="left">순서형 (Ordinal)</td>
<td align="left">순서 있음, 간격 의미 없음</td>
<td align="left">만족도(좋음/보통/나쁨), 학점(A/B/C), 계급</td>
</tr>
<tr>
<td align="left"><strong>양적 데이터</strong> (Quantitative / 수치형)</td>
<td align="left"><strong>이산형</strong> (Discrete)</td>
<td align="left">셀 수 있음, 정수 단위</td>
<td align="left">자녀 수, 사람 수, 주사위 눈, 상품 개수</td>
</tr>
<tr>
<td align="left"></td>
<td align="left"><strong>연속형</strong> (Continuous)</td>
<td align="left">셀 수 없음, 실수 범위</td>
<td align="left">키, 몸무게, 온도, 시간, 거리, 가격</td>
</tr>
</tbody></table>
<hr />
<h1 id="히스토그램">히스토그램</h1>
<ul>
<li>데이터 분포를 시각적으로 표현하는 그래프</li>
<li>연속적인 데이터를 구간으로 나타내 표현(예: 도수분포표)</li>
<li>각 구간의 빈도수를 막대의 높이로 나타냄</li>
<li>데이터의 전체적인 분포와 특성 한눈에 파악 가능</li>
</ul>
<hr />
<h1 id="데이터의-대푯값">데이터의 대푯값</h1>
<ul>
<li>평균, 중앙값, 최빈값</li>
</ul>
<hr />
<h1 id="평균-중앙값-최빈값">평균 중앙값, 최빈값</h1>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left">정의</th>
<th align="left">장점</th>
<th align="left">단점</th>
<th align="left">예시 상황</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>평균값 (Mean)</strong></td>
<td align="left">모든 값을 더해 개수로 나눈 값</td>
<td align="left">계산 간단, 널리 사용됨</td>
<td align="left"><strong>극단값(이상치)에 민감</strong>함</td>
<td align="left">시험 점수 평균, 월급 평균</td>
</tr>
<tr>
<td align="left"><strong>중앙값 (Median)</strong></td>
<td align="left">크기 순서대로 정렬한 후 <strong>가운데 값</strong></td>
<td align="left">이상치에 강함, 데이터가 비대칭일 때 유리</td>
<td align="left">계산 복잡, 데이터가 정렬돼야 함</td>
<td align="left">연봉, 주택 가격 분석</td>
</tr>
<tr>
<td align="left"><strong>최빈값 (Mode)</strong></td>
<td align="left">가장 <strong>자주 등장한 값</strong></td>
<td align="left">범주형(질적) 데이터에도 사용 가능</td>
<td align="left">데이터에 따라 존재하지 않을 수 있음</td>
<td align="left">고객 선호 색상, 인기 제품 크기</td>
</tr>
</tbody></table>
<hr />
<h1 id="형태별로-분포-정리">형태별로 분포 정리</h1>
<table>
<thead>
<tr>
<th align="left">분포 형태</th>
<th align="left">설명</th>
<th align="left">평균, 중앙값, 최빈값 관계</th>
<th align="left">왜도(Skewness)</th>
<th align="left">예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>좌우대칭 분포</strong><br />(정규분포)</td>
<td align="left">가운데를 기준으로 좌우가 대칭</td>
<td align="left">평균 = 중앙값 = 최빈값</td>
<td align="left">0</td>
<td align="left">키, IQ 등</td>
</tr>
<tr>
<td align="left"><strong>왼쪽으로 꼬리 김</strong><br />(<strong>왼쪽 비대칭</strong> / <strong>음의 왜도</strong>)</td>
<td align="left"><strong>작은 값 쪽에 긴 꼬리</strong>가 있음</td>
<td align="left">평균 &lt; 중앙값 &lt; 최빈값</td>
<td align="left">음수(-)</td>
<td align="left">시험에서 대부분 고득점</td>
</tr>
<tr>
<td align="left"><strong>오른쪽으로 꼬리 김</strong><br />(<strong>오른쪽 비대칭</strong> / <strong>양의 왜도</strong>)</td>
<td align="left"><strong>큰 값 쪽에 긴 꼬리</strong>가 있음</td>
<td align="left">평균 &gt; 중앙값 &gt; 최빈값</td>
<td align="left">양수(+)</td>
<td align="left">연봉, 부동산 가격, 대여량</td>
</tr>
</tbody></table>
<hr />
<h1 id="4분위수">4분위수</h1>
<ul>
<li>데이터를 크기 순서로 정렬했을 때, 이를 네 개의 구간으로 나누는 기준값</li>
<li>전체 데이터를 25% 단위로 나눈 지점</li>
</ul>
<hr />
<h1 id="4분위수-구성">4분위수 구성</h1>
<table>
<thead>
<tr>
<th align="left">분위수</th>
<th align="left">기호</th>
<th align="left">위치</th>
<th align="left">의미</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>1사분위수 (Q1)</strong></td>
<td align="left">Q1</td>
<td align="left">25% 지점</td>
<td align="left">**하위 25%**까지의 값</td>
</tr>
<tr>
<td align="left"><strong>2사분위수 (Q2)</strong></td>
<td align="left">Q2</td>
<td align="left">50% 지점</td>
<td align="left"><strong>중앙값 (Median)</strong></td>
</tr>
<tr>
<td align="left"><strong>3사분위수 (Q3)</strong></td>
<td align="left">Q3</td>
<td align="left">75% 지점</td>
<td align="left"><strong>상위 25% 미만</strong>까지의 값</td>
</tr>
<tr>
<td align="left"><strong>4사분위수</strong></td>
<td align="left">-</td>
<td align="left">100%</td>
<td align="left">데이터의 최대값</td>
</tr>
</tbody></table>
<hr />
<h1 id="iqr과-이상치-반별-기준">IQR과 이상치 반별 기준</h1>
<ul>
<li>사분위 범위: 중앙 50%에 해당하는 범위<ul>
<li><code>IQR = Q3 - Q1</code></li>
</ul>
</li>
<li>이상치 반별 기준 (박스플롯 기반)</li>
</ul>
<table>
<thead>
<tr>
<th align="left">기준</th>
<th align="left">조건</th>
</tr>
</thead>
<tbody><tr>
<td align="left">하한 (Lower Bound)</td>
<td align="left">Q1 - 1.5 × IQR</td>
</tr>
<tr>
<td align="left">상한 (Upper Bound)</td>
<td align="left">Q3 + 1.5 × IQR</td>
</tr>
<tr>
<td align="left">이 범위를 벗어난 값</td>
<td align="left"><strong>이상치(Outlier)</strong> 로 간주됨</td>
</tr>
</tbody></table>
<hr />
<h1 id="상자수염도">상자수염도</h1>
<ul>
<li>데이터를 5가지 요약값(최소, Q1, Q2, Q3, 최대)으로 표현하며, 중앙값과 사분위수, 이상치까지 시각적으로 한 번에 보여주는 그래프</li>
</ul>