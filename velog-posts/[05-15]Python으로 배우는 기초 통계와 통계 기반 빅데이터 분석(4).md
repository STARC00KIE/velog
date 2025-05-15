<h1 id="이산확률변수-vs-연속확률변수의-평균-분산-표준편차">이산확률변수 vs 연속확률변수의 평균, 분산, 표준편차</h1>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left">기댓값 (평균) E[X]</th>
<th align="left">분산 Var(X)</th>
<th align="left">표준편차 SD(X)</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>이산확률변수</strong></td>
<td align="left">$E[X] = \sum x_i \cdot P(X = x_i)$</td>
<td align="left">$\mathrm{Var}(X) = \sum (x_i - \mu)^2 \cdot P(X = x_i)$</td>
<td align="left">$\sigma = \sqrt{\mathrm{Var}(X)}$</td>
</tr>
<tr>
<td align="left"><strong>연속확률변수</strong></td>
<td align="left">$E[X] = \int_{-\infty}^{\infty} x \cdot f(x) , dx$</td>
<td align="left">$\mathrm{Var}(X) = \int_{-\infty}^{\infty} (x - \mu)^2 \cdot f(x) , dx$</td>
<td align="left">$\sigma = \sqrt{\mathrm{Var}(X)}$</td>
</tr>
</tbody></table>
<hr />
<h1 id="누적분포함수">누적분포함수</h1>
<ul>
<li>확률변수 X가 어떤 값 x 이하일 확률을 나타내는 함수</li>
<li>Cumulative Distribution Function, 줄여서 CDF</li>
<li><code>F(x) = P(X≤x)</code></li>
</ul>
<hr />
<h1 id="주요-확률분포의-누적분포함수cdf-평균-분산-표준편차">주요 확률분포의 누적분포함수(CDF), 평균, 분산, 표준편차</h1>
<table>
<thead>
<tr>
<th>분포</th>
<th>CDF $F(x)$</th>
<th>평균 $E(X)$</th>
<th>분산 $Var(X)$</th>
<th>표준편차 $\sigma$</th>
</tr>
</thead>
<tbody><tr>
<td><strong>이항분포</strong> $B(n, p)$</td>
<td>$\displaystyle F(x) = P(X \leq x) = \sum_{k=0}^{x} \binom{n}{k}p^k(1-p)^{n-k}$</td>
<td>$np$</td>
<td>$np(1 - p)$</td>
<td>$\sqrt{np(1 - p)}$</td>
</tr>
<tr>
<td><strong>정규분포</strong> $N(\mu, \sigma^2)$</td>
<td>$\displaystyle F(x) = \frac{1}{2}\left[1 + \text{erf}\left(\frac{x - \mu}{\sigma \sqrt{2}}\right)\right]$</td>
<td>$\mu$</td>
<td>$\sigma^2$</td>
<td>$\sigma$</td>
</tr>
<tr>
<td><strong>포아송분포</strong> $\text{Poisson}(\lambda)$</td>
<td>$\displaystyle F(x) = \sum_{k=0}^{x} \frac{e^{-\lambda} \lambda^k}{k!}$</td>
<td>$\lambda$</td>
<td>$\lambda$</td>
<td>$\sqrt{\lambda}$</td>
</tr>
<tr>
<td><strong>지수분포</strong> $Exp(\lambda)$</td>
<td>$\displaystyle F(x) = 1 - e^{-\lambda x}$, $x \geq 0$</td>
<td>$\frac{1}{\lambda}$</td>
<td>$\frac{1}{\lambda^2}$</td>
<td>$\frac{1}{\lambda}$</td>
</tr>
<tr>
<td><strong>균등분포</strong> $U(a, b)$</td>
<td>$\displaystyle F(x) = \frac{x - a}{b - a}, \quad a \leq x \leq b$</td>
<td>$\frac{a + b}{2}$</td>
<td>$\frac{(b - a)^2}{12}$</td>
<td>$\frac{b - a}{\sqrt{12}}$</td>
</tr>
</tbody></table>
<hr />
<h1 id="확률질량함수">확률질량함수</h1>
<ul>
<li>이산형 확률변수에서, 특정한 값 𝑥가 나올 확률을 나타내는 함수</li>
<li>PMF, Probability Mass Function</li>
<li>이산형 확률변수에서만 정의됨 (예: 동전, 주사위)</li>
</ul>
<hr />
<h1 id="확률밀도함수">확률밀도함수</h1>
<ul>
<li>연속형 확률변수에서, 특정 값 근처의 확률 밀도를 나타내는 함수</li>
<li>PDF, Probability Density Function</li>
<li>연속형 확률변수에서 정의됨</li>
</ul>
<hr />
<h1 id="pdf-vs-pmf">PDF vs PMF</h1>
<table>
<thead>
<tr>
<th>항목</th>
<th>PMF (이산형)</th>
<th>PDF (연속형)</th>
</tr>
</thead>
<tbody><tr>
<td>정의</td>
<td>$P(X = x)$</td>
<td>$P(a \leq X \leq b) = \int_a^b f(x)dx$</td>
</tr>
<tr>
<td>적용 대상</td>
<td>이산형 확률변수</td>
<td>연속형 확률변수</td>
</tr>
<tr>
<td>확률 계산</td>
<td>각 값에 직접 적용</td>
<td>구간의 면적(적분)으로 계산</td>
</tr>
<tr>
<td>개별 값의 확률</td>
<td>$&gt; 0$ 가능</td>
<td>항상 0</td>
</tr>
<tr>
<td>전체 합</td>
<td>$\sum p(x) = 1$</td>
<td>$\int f(x) dx = 1$</td>
</tr>
</tbody></table>
<hr />
<h1 id="주요-확률분포-요약표">주요 확률분포 요약표</h1>
<table>
<thead>
<tr>
<th>분포</th>
<th>유형</th>
<th>사용 예시</th>
<th>평균 $E(X)$</th>
<th>분산 $Var(X)$</th>
<th>PMF or PDF</th>
<th>CDF</th>
</tr>
</thead>
<tbody><tr>
<td><strong>이항분포</strong> $B(n, p)$</td>
<td>이산</td>
<td>n번 실험 중 성공 횟수 (ex: 동전 던지기)</td>
<td>$np$</td>
<td>$np(1-p)$</td>
<td>$\binom{n}{k} p^k (1-p)^{n-k}$</td>
<td>$\sum_{k=0}^{x} \binom{n}{k} p^k (1-p)^{n-k}$</td>
</tr>
<tr>
<td><strong>베르누이분포</strong></td>
<td>이산</td>
<td>단일 시행의 성공/실패 (ex: 동전 앞/뒤)</td>
<td>$p$</td>
<td>$p(1-p)$</td>
<td>$p^x (1-p)^{1-x}$</td>
<td>$F(0) = 1-p,\ F(1) = 1$</td>
</tr>
<tr>
<td><strong>포아송분포</strong> $\text{Poisson}(\lambda)$</td>
<td>이산</td>
<td>단위 시간/공간당 사건 수 (ex: 시간당 고객 수)</td>
<td>$\lambda$</td>
<td>$\lambda$</td>
<td>$\frac{e^{-\lambda} \lambda^k}{k!}$</td>
<td>$\sum_{k=0}^{x} \frac{e^{-\lambda} \lambda^k}{k!}$</td>
</tr>
<tr>
<td><strong>정규분포</strong> $N(\mu, \sigma^2)$</td>
<td>연속</td>
<td>자연 현상, 키, 시험 점수 등</td>
<td>$\mu$</td>
<td>$\sigma^2$</td>
<td>$\frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$</td>
<td>$\frac{1}{2}\left[1 + \text{erf}\left(\frac{x - \mu}{\sigma\sqrt{2}}\right)\right]$</td>
</tr>
<tr>
<td><strong>표준 정규분포</strong> $N(0, 1)$</td>
<td>연속</td>
<td>정규화된 데이터</td>
<td>0</td>
<td>1</td>
<td>위와 동일 (단 $\mu = 0, \sigma = 1$)</td>
<td>위와 동일</td>
</tr>
<tr>
<td><strong>지수분포</strong> $Exp(\lambda)$</td>
<td>연속</td>
<td>사건 간 시간 간격 (ex: 고장까지 시간)</td>
<td>$\frac{1}{\lambda}$</td>
<td>$\frac{1}{\lambda^2}$</td>
<td>$\lambda e^{-\lambda x}$</td>
<td>$1 - e^{-\lambda x}$</td>
</tr>
<tr>
<td><strong>균등분포</strong> $U(a, b)$</td>
<td>연속</td>
<td>균등하게 분포된 값 (ex: 난수)</td>
<td>$\frac{a+b}{2}$</td>
<td>$\frac{(b-a)^2}{12}$</td>
<td>$\frac{1}{b - a},\ a \leq x \leq b$</td>
<td>$\frac{x - a}{b - a}$</td>
</tr>
</tbody></table>
<hr />
<h1 id="주요-확률분포-사용-상황-요약표">주요 확률분포 사용 상황 요약표</h1>
<table>
<thead>
<tr>
<th>분포</th>
<th>사용 상황</th>
<th>대표 사례</th>
<th>사용 조건</th>
</tr>
</thead>
<tbody><tr>
<td><strong>이항분포</strong> $B(n, p)$</td>
<td>정해진 횟수의 시행에서 성공 횟수</td>
<td>10번 동전 던져 앞면 나올 횟수</td>
<td>- 시행 횟수 $n$ 고정<br />- 매 시행 독립<br />- 성공 확률 $p$ 동일</td>
</tr>
<tr>
<td><strong>베르누이분포</strong></td>
<td>단 한 번의 성공/실패 시도</td>
<td>동전 1번 던져 앞면 나올 확률</td>
<td>- 단일 시행<br />- 두 가지 결과만 가능 (성공/실패)</td>
</tr>
<tr>
<td><strong>포아송분포</strong> $\text{Poisson}(\lambda)$</td>
<td>단위 시간/공간에서 사건 발생 횟수</td>
<td>1시간 동안 도착한 고객 수</td>
<td>- 사건이 독립적으로 발생<br />- 평균 발생률 $\lambda$ 일정</td>
</tr>
<tr>
<td><strong>정규분포</strong> $N(\mu, \sigma^2)$</td>
<td>연속적이고 자연스러운 수치 데이터 분석</td>
<td>키, 체중, 시험 점수</td>
<td>- 데이터가 중심을 기준으로 대칭<br />- 큰 수의 법칙으로 수렴</td>
</tr>
<tr>
<td><strong>표준정규분포</strong> $N(0, 1)$</td>
<td>정규분포 데이터를 정규화한 경우</td>
<td>Z-점수 계산, 통계 검정</td>
<td>- 정규분포 데이터를 평균 0, 분산 1로 변환</td>
</tr>
<tr>
<td><strong>지수분포</strong> $Exp(\lambda)$</td>
<td>사건 사이의 시간 간격 분석</td>
<td>다음 버스까지 대기 시간</td>
<td>- 사건 사이 시간이 독립<br />- 일정한 평균 간격</td>
</tr>
<tr>
<td><strong>균등분포</strong> $U(a, b)$</td>
<td>모든 값이 똑같은 확률일 때</td>
<td>랜덤 숫자 생성, 무작위 추출</td>
<td>- 어떤 값도 더 유리하거나 불리하지 않음<br />- 확률이 일정하게 분포</td>
</tr>
</tbody></table>
<ul>
<li>반복적 시도: 이항 or 베르누이 분포</li>
<li>시간당 사건 수: 포아송분포</li>
<li>자연적 수치 데이터: 정규분포</li>
<li>다음 사건까지 시간: 지수분포</li>
<li>완전히 무작위한 값: 균등분포</li>
</ul>