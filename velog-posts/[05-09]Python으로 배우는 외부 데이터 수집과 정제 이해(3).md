<h1 id="matplotlib">Matplotlib</h1>
<ul>
<li>Python에서 데이터를 시각적으로 표현하기 위한 대표적인 시각화 라이브러리</li>
<li>다양한 그래프(선, 막대, 산점도, 히스토그램 등)를 정밀하게 커스터마이징할 수 있음</li>
<li>구조<ul>
<li>pyplot: 인터페이스(주로 사용하는 부분)</li>
<li>figure: 전체 도화지</li>
<li>axes: subplot 단위</li>
<li>backend: 화면 출력, 이미지 저장 담당</li>
</ul>
</li>
</ul>
<hr />
<h1 id="한글-폰트-설정-colab-환경-기준">한글 폰트 설정 (Colab 환경 기준)</h1>
<pre><code class="language-python">!pip install koreanize-matplotlib
import koreanize_matplotlib</code></pre>
<ul>
<li>그래프에서 한글이 깨지지 않게 처리함</li>
</ul>
<hr />
<h1 id="figure-subplot-생성방법">figure, subplot 생성방법</h1>
<h2 id="1-단계별-생성">1. 단계별 생성</h2>
<pre><code class="language-python">fig = plt.figure(figsize=(6,3))  # 도화지 생성
ax1 = fig.add_subplot(2,2,1)     # 2x2 그리드 중 1번 위치</code></pre>
<h2 id="2-한-번에-생성">2. 한 번에 생성</h2>
<pre><code class="language-python">fig, axes = plt.subplots(2, 3, figsize=(6, 3))  # 2행 3열
axes[0,0].plot(data)</code></pre>
<hr />
<h1 id="matplotlib-기본-사용-흐름">matplotlib 기본 사용 흐름</h1>
<pre><code class="language-python">import matplotlib.pyplot as plt

x = [1, 2, 3, 4]
y = [10, 20, 25, 30]

plt.plot(x, y)           # 선 그래프
plt.title('예제 그래프')   # 제목
plt.xlabel('X축')        # x축 이름
plt.ylabel('Y축')        # y축 이름
plt.grid(True)            # 격자 출력 여부 확인
plt.show()               # 그래프 출력</code></pre>
<hr />
<h1 id="matplotlib-주요-메서드-정리">matplotlib 주요 메서드 정리</h1>
<table>
<thead>
<tr>
<th align="left">메서드</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>plt.plot()</code></td>
<td align="left">선 그래프 그리기 (x, y)</td>
</tr>
<tr>
<td align="left"><code>plt.bar()</code> / <code>plt.barh()</code></td>
<td align="left">막대 그래프 (수직/수평)</td>
</tr>
<tr>
<td align="left"><code>plt.scatter()</code></td>
<td align="left">산점도</td>
</tr>
<tr>
<td align="left"><code>plt.hist()</code></td>
<td align="left">히스토그램</td>
</tr>
<tr>
<td align="left"><code>plt.boxplot()</code></td>
<td align="left">박스플롯 (이상치 시각화)</td>
</tr>
<tr>
<td align="left"><code>plt.pie()</code></td>
<td align="left">파이차트</td>
</tr>
<tr>
<td align="left"><code>plt.imshow()</code></td>
<td align="left">이미지나 행렬 시각화</td>
</tr>
<tr>
<td align="left"><code>plt.title()</code></td>
<td align="left">그래프 제목 설정</td>
</tr>
<tr>
<td align="left"><code>plt.xlabel()</code> / <code>plt.ylabel()</code></td>
<td align="left">x축 / y축 레이블 지정</td>
</tr>
<tr>
<td align="left"><code>plt.xticks()</code> / <code>plt.yticks()</code></td>
<td align="left">축 눈금 직접 설정</td>
</tr>
<tr>
<td align="left"><code>plt.xlim()</code> / <code>plt.ylim()</code></td>
<td align="left">축 범위 수동 지정</td>
</tr>
<tr>
<td align="left"><code>plt.legend()</code></td>
<td align="left">범례 표시</td>
</tr>
<tr>
<td align="left"><code>plt.grid()</code></td>
<td align="left">그리드(격자선) 표시 여부</td>
</tr>
<tr>
<td align="left"><code>plt.text()</code></td>
<td align="left">그래프 안에 텍스트 표시</td>
</tr>
<tr>
<td align="left"><code>plt.annotate()</code></td>
<td align="left">화살표로 설명 텍스트 추가</td>
</tr>
<tr>
<td align="left"><code>plt.figure()</code></td>
<td align="left">새로운 figure(도화지) 생성</td>
</tr>
<tr>
<td align="left"><code>plt.subplots()</code></td>
<td align="left">여러 subplot 생성 (figure + axes 반환)</td>
</tr>
<tr>
<td align="left"><code>plt.subplot()</code></td>
<td align="left">위치 지정해 subplot 추가 (단순 버전)</td>
</tr>
<tr>
<td align="left"><code>plt.tight_layout()</code></td>
<td align="left">겹치는 그래프 요소 자동 정리</td>
</tr>
<tr>
<td align="left"><code>plt.savefig()</code></td>
<td align="left">그래프를 이미지 파일로 저장</td>
</tr>
<tr>
<td align="left"><code>plt.show()</code></td>
<td align="left">화면에 그래프 출력 (Jupyter에선 꼭 필요!)</td>
</tr>
<tr>
<td align="left"><code>plt.clf()</code></td>
<td align="left">현재 figure 초기화</td>
</tr>
<tr>
<td align="left"><code>plt.close()</code></td>
<td align="left">현재 창 닫기</td>
</tr>
</tbody></table>
<hr />
<h1 id="그래프-정리">그래프 정리</h1>
<table>
<thead>
<tr>
<th align="left">그래프 종류</th>
<th align="left">데이터 유형</th>
<th align="left">추천 상황</th>
</tr>
</thead>
<tbody><tr>
<td align="left">선 그래프</td>
<td align="left">수치형 (시간 기준)</td>
<td align="left">시간에 따른 <strong>연속적 변화</strong> (예: 일별 매출, 온도 변화)</td>
</tr>
<tr>
<td align="left">수직 막대 그래프</td>
<td align="left">범주형 + 수치형</td>
<td align="left"><strong>카테고리별 수치 비교</strong> (예: 지역별 매출, 부서별 인원수)</td>
</tr>
<tr>
<td align="left">수평 막대 그래프</td>
<td align="left">범주형 + 수치형</td>
<td align="left">범주 이름이 길거나 <strong>많을 때</strong> 보기 편함</td>
</tr>
<tr>
<td align="left">히스토그램</td>
<td align="left">수치형 (1개 변수)</td>
<td align="left"><strong>분포 확인</strong> (예: 나이, 점수 등 데이터의 빈도 분포)</td>
</tr>
<tr>
<td align="left">박스플롯</td>
<td align="left">수치형 + (선택적 범주형 그룹)</td>
<td align="left"><strong>분포와 이상치 탐지</strong> (예: 과목별 점수 분포)</td>
</tr>
<tr>
<td align="left">커널 밀도 그래프</td>
<td align="left">수치형</td>
<td align="left">부드러운 <strong>연속 분포 곡선</strong> 시각화</td>
</tr>
<tr>
<td align="left">면적 그래프</td>
<td align="left">수치형 (시간 기준)</td>
<td align="left">누적량/추세 표현에 적합 (예: 누적 대여량)</td>
</tr>
<tr>
<td align="left">파이 그래프</td>
<td align="left">범주형</td>
<td align="left"><strong>전체 대비 비율 표현</strong> (소수 항목일 때만 추천)</td>
</tr>
<tr>
<td align="left">산점도</td>
<td align="left">수치형 2개</td>
<td align="left">두 수치형 변수 간 <strong>관계/상관</strong> 파악</td>
</tr>
<tr>
<td align="left">고밀도 산점도</td>
<td align="left">수치형 2개</td>
<td align="left">데이터가 많을 때 <strong>산점도 겹침 해결</strong>, 밀도 파악용</td>
</tr>
</tbody></table>