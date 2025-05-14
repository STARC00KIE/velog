<h1 id="시행-표본공간-근원사건-사건">시행, 표본공간, 근원사건, 사건</h1>
<table>
<thead>
<tr>
<th align="left">용어</th>
<th align="left">정의</th>
<th align="left">설명</th>
<th align="left">예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>시행 (Trial)</strong></td>
<td align="left">어떤 실험이나 관찰을 1회 수행하는 것</td>
<td align="left">결과가 불확실한 행위</td>
<td align="left">동전 한 번 던지기, 주사위 한 번 굴리기</td>
</tr>
<tr>
<td align="left"><strong>표본공간 (Sample space, Ω)</strong></td>
<td align="left">가능한 모든 결과의 집합</td>
<td align="left">시행 결과 전체 모음</td>
<td align="left">동전 던지기: Ω = {앞, 뒤}<br />주사위: Ω = {1,2,3,4,5,6}</td>
</tr>
<tr>
<td align="left"><strong>근원사건 (Elementary event)</strong></td>
<td align="left">표본공간을 구성하는 한 원소</td>
<td align="left">단일 결과</td>
<td align="left">주사위에서 1이 나올 경우: {1}</td>
</tr>
<tr>
<td align="left"><strong>사건 (Event)</strong></td>
<td align="left">표본공간의 부분집합 (하나 이상의 결과 포함 가능)</td>
<td align="left">결과 집합</td>
<td align="left">주사위 짝수: {2, 4, 6}<br />3 이하: {1, 2, 3}</td>
</tr>
<tr>
<td align="left">- 시행을 하면 표본공간에서 어떤 근원사건이 하나 발생함</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 여러 근원사건의 집합이 하나의 사건이 됨</td>
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
<td align="left"># 독립시행, 종속시행, 복원추출, 비복원추출</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">용어</td>
<td align="left">정의</td>
<td align="left">결과 간 관계</td>
<td align="left">예시</td>
</tr>
<tr>
<td align="left">:--------</td>
<td align="left">:--------------------------</td>
<td align="left">:-------------------------</td>
<td align="left">:--------------------------</td>
</tr>
<tr>
<td align="left"><strong>독립시행</strong></td>
<td align="left">이전 결과가 다음 결과에 <strong>영향을 주지 않음</strong></td>
<td align="left">결과들이 <strong>서로 무관함</strong></td>
<td align="left">동전을 두 번 던지기 (앞·뒤는 서로 영향 없음)</td>
</tr>
<tr>
<td align="left"><strong>종속시행</strong></td>
<td align="left">앞의 결과가 뒤에 <strong>영향을 줌</strong></td>
<td align="left"><strong>조건부 확률</strong> 필요</td>
<td align="left">카드 한 장 뽑고 그대로 두지 않고 또 뽑을 때</td>
</tr>
<tr>
<td align="left"><strong>복원추출</strong></td>
<td align="left">뽑은 뒤 <strong>다시 넣고</strong> 다음을 뽑음</td>
<td align="left">각 시행마다 조건 동일 → <strong>독립시행</strong> 가능</td>
<td align="left">주머니에서 공 뽑고 다시 넣는 경우</td>
</tr>
<tr>
<td align="left"><strong>비복원추출</strong></td>
<td align="left">뽑은 뒤 <strong>다시 넣지 않고</strong> 다음을 뽑음</td>
<td align="left">남은 개수 줄어듦 → <strong>종속시행</strong></td>
<td align="left">주머니에서 공 뽑고 버리는 경우</td>
</tr>
<tr>
<td align="left">- 모집단이 매우 크고 표본이 작을 경우, <strong>비복원추출도 독립처럼 간주</strong>하기도 함</td>
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
<td align="left"># 독립시행의 확률</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 두 사건 A, B가 서로 영향을 주지 않을 때, A와 B가 <strong>동시에 일어날 확률</strong>은 각각의 확률을 곱한 것</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 공식:</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left"><code>P(A ∩ B) = P(A) × P(B)</code></td>
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
<td align="left"># 반복시행의 확률 (독립시행 n번 반복)</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 같은 실험을 독립적으로 여러 번 반복하는 경우</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 공식:</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left"><code>P(사건 A가 n번 연속 발생) = P(A)^n</code></td>
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
<td align="left"># 조건부 확률</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 어떤 사건이 이미 일어난 상황에서 다른 사건이 일어날 확률</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 공식:</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">`P(A</td>
<td align="left">B) = P(A ∩ B) / P(B)` (B가 일어났을 때, A가 일어날 확률)</td>
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
<td align="left"># 확률의 곱셈정리(Multiplication Rule)</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 두 사건 A와 B가 모두 일어날 확률:</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">1. 기본 공식: ` P(A ∩ B) = P(A) × P(B</td>
<td align="left">A)`</td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">2. A와 B가 독립일 때: `P(B</td>
<td align="left">A) = P(B)<code>,</code>P(A ∩ B) = P(A) × P(B)`</td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">3. A와 B가 종속일 때:</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- B의 확률이 A에 따라 달라짐 -&gt; 조건부 확률 사용해야 함</td>
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
<td align="left"># 베이즈 정리</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 어떤 조건부 확률을 반대로 구하는 공식</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- **P(B</td>
<td align="left">A)*<em>를 알 때 *</em>P(A</td>
<td align="left">B)**를 구할 수 있도록 해주는 도구</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 공식: `P(A</td>
<td align="left">B) = [P(B</td>
<td align="left">A) × P(A)] / P(B)`</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 베이즈 정리가 필요한 상황:</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 원인 -&gt; 결과 확률은 아는데, 결과 -&gt; 원인 확률이 궁금할 때 사용함</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 실제 검출보다 오탐이 많을 때 꼭 필요함 (유병률 낮은 병, 마약 검사 등)</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">----</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left"># 확률변수 (Random Variable)</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 시행의 결과를 수치로 대응시키는 함수</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 우연한 결과를 숫자로 바꾸는 것 -&gt; 확률을 수학적으로 다룰 수 있도록 변환해주는 개념</td>
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
<td align="left"># 확률분포 (Probability Distribution)</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">- 확률변수가 어떤 값을 가질 확률을 나타낸 것</td>
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
<td align="left"># 이산확률변수 vs 연속확률변수</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">구분</td>
<td align="left">이산확률변수 (Discrete)</td>
<td align="left">연속확률변수 (Continuous)</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">:----</td>
<td align="left">:----------------</td>
<td align="left">:------------------</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">값의 종류</td>
<td align="left">셀 수 있음 (정수)</td>
<td align="left">셀 수 없음 (실수 구간)</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">확률분포</td>
<td align="left"><strong>확률 질량 함수(PMF)</strong></td>
<td align="left"><strong>확률 밀도 함수(PDF)</strong></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">예시</td>
<td align="left">동전, 주사위, 사람 수</td>
<td align="left">키, 몸무게, 온도, 시간</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">시각화</td>
<td align="left">막대그래프</td>
<td align="left">곡선 그래프 (적분으로 확률 계산)</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">---</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left"># 이산확률변수의 대표적 종류들</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">분포 이름</td>
<td align="left">정의</td>
<td align="left">사용 조건</td>
<td align="left">예시</td>
</tr>
<tr>
<td align="left">:----------</td>
<td align="left">:-------------------</td>
<td align="left">:----------------</td>
<td align="left">:---------------------</td>
</tr>
<tr>
<td align="left"><strong>베르누이 분포</strong></td>
<td align="left">2가지 결과 중 하나 (성공/실패)</td>
<td align="left">1회 시행, 성공 확률 p</td>
<td align="left">동전 던져 앞면(1)/뒷면(0)</td>
</tr>
<tr>
<td align="left"><strong>이항 분포</strong></td>
<td align="left">베르누이 시행을 n번 반복</td>
<td align="left">n번 독립시행, 동일한 p</td>
<td align="left">동전 10번 던져 앞면 개수</td>
</tr>
<tr>
<td align="left"><strong>기하 분포</strong></td>
<td align="left">처음 성공이 나올 때까지 반복한 횟수</td>
<td align="left">베르누이 반복, 최초 성공 시점</td>
<td align="left">동전을 계속 던져 처음 앞면까지 몇 번?</td>
</tr>
<tr>
<td align="left"><strong>포아송 분포</strong></td>
<td align="left">단위 시간/공간당 발생 횟수</td>
<td align="left">희귀 사건, 독립적 발생</td>
<td align="left">1시간 동안 고객 3명 올 확률</td>
</tr>
<tr>
<td align="left"><strong>초기하 분포</strong></td>
<td align="left">복원 없이 추출된 성공 개수</td>
<td align="left">비복원 추출</td>
<td align="left">카드 5장 뽑을 때 에이스 수</td>
</tr>
</tbody></table>