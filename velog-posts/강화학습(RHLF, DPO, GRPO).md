<h1 id="1-rlhf---dpo---grpo-개념-및-차이">1. RLHF - DPO - GRPO 개념 및 차이</h1>
<h2 id="a-기본-배경지식">a. 기본 배경지식</h2>
<ul>
<li>LLM은 사전학습 이후에 다양한 방법으로 후속 최적화를 진행함</li>
<li><code>SFT</code>와 <code>RLHF</code> 2가지 존재</li>
<li>보통 학습 순서는 <code>(사전학습 -&gt; SFT -&gt; RLHF)</code>로 진행됨</li>
<li>최종적으로 얻은 <code>RLHF</code> 까지 마친 모델을 <code>policy model</code> 혹은 <code>align model</code> 이라고 함
<a href="https://mermaid.live/edit#pako:eNpNkL1u2zAURl-FuF5aQDYs64cSUxiwHRgZPAROplQdaPHSJiyRAkW1SQwvRafuHbLlAbL2rdx3KC0jaDnxI79zSNwDlEYgMNha3uzIal1o4tfscwGn72-n1x9_fr2cfv7-tLHTD7cWneVKK739WMAXMhxOydwX75b3_f1d16D9qloUZKk0Du-79-pFOu-JhSfWq5tlj6xRaWlsiTVqR1bI7Rkh0pqa3HQ112SJKDa83F80F1FZ8ba9Rklahw2RqqrYAFGmUgats2aPbEA5pz6WpjKWDcabSORhII12w2-otjvHNqYSV__pyCyYB4veeAWBH4cSwJztMIAabc3PEQ5noAC38_8tgPmt4HZfQKGPnmm4fjCmfses6bY7YJJXrU9dI7jDa8X9oP9VUAu0C9NpByzvDcAO8AgszMNRRMM0yyZxkqVhlAXw5I8jOhqnk3g8ybOExlmSHQN47h8dj2hO4yhNkzhJKQ2z5PgXyzmZIQ"><img alt="" src="https://mermaid.ink/img/pako:eNpNkL1u2zAURl-FuF5aQDYs64cSUxiwHRgZPAROplQdaPHSJiyRAkW1SQwvRafuHbLlAbL2rdx3KC0jaDnxI79zSNwDlEYgMNha3uzIal1o4tfscwGn72-n1x9_fr2cfv7-tLHTD7cWneVKK739WMAXMhxOydwX75b3_f1d16D9qloUZKk0Du-79-pFOu-JhSfWq5tlj6xRaWlsiTVqR1bI7Rkh0pqa3HQ112SJKDa83F80F1FZ8ba9Rklahw2RqqrYAFGmUgats2aPbEA5pz6WpjKWDcabSORhII12w2-otjvHNqYSV__pyCyYB4veeAWBH4cSwJztMIAabc3PEQ5noAC38_8tgPmt4HZfQKGPnmm4fjCmfses6bY7YJJXrU9dI7jDa8X9oP9VUAu0C9NpByzvDcAO8AgszMNRRMM0yyZxkqVhlAXw5I8jOhqnk3g8ybOExlmSHQN47h8dj2hO4yhNkzhJKQ2z5PgXyzmZIQ?type=png" /></a><h2 id="b-rlhfreinforcement-learning-from-human-feedback-인간-피드백-기반-강화학습">b. RLHF(Reinforcement Learning from Human Feedback, 인간 피드백 기반 강화학습)</h2>
<h3 id="--개요">- 개요</h3>
</li>
<li>언어모델이 단순히 다음 단어를 예측하는 것이 아니라 사람이 보기 좋은 답변, 정확한 답변을 생성하도록 학습시키는 과정<h3 id="--기본-데이터-구조">- 기본 데이터 구조</h3>
<table>
<thead>
<tr>
<th>단계</th>
<th>설명</th>
<th>사용 데이터</th>
</tr>
</thead>
<tbody><tr>
<td><strong>① SFT</strong></td>
<td>지도학습으로 기본 대화 능력 학습</td>
<td>(prompt, response)</td>
</tr>
<tr>
<td><strong>② RM 학습</strong></td>
<td>인간 선호 기반 보상모델 훈련</td>
<td>(prompt, chosen, rejected) → (prompt, response, reward)</td>
</tr>
<tr>
<td><strong>③ PPO 강화학습</strong></td>
<td>보상모델을 이용해 정책(모델)을 개선</td>
<td>(prompt, response) + reward model 평가 결과</td>
</tr>
</tbody></table>
</li>
</ul>
<h3 id="--전체-학습-구조">- 전체 학습 구조</h3>
<ul>
<li>학습 과정이 SFT -&gt; RM -&gt; PRO로 진행됨
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/d1e0abb3-a4af-452f-9340-2dd0d993ee7d/image.png" /><h4 id="sftsupervised-fine-tuning">SFT(Supervised Fine-Tuning)</h4>
</li>
<li>인간이 답변한 &quot;좋은 답변&quot; 데이터로 지도학습 진행</li>
<li>모델이 기본적인 언어 이해와 생성 능력을 안정화시킴</li>
<li>모델이 기본적으로 &quot;질문에 답변하는&quot; 습관을 가질수 있도록 학습시키는 과정<h4 id="rmreward-model-학습">RM(Reward Model) 학습</h4>
</li>
<li>같은 프롬프트에 대해 두 개의 답변을 주고 인간이 어떤 답변이 더 좋은지 선택함</li>
<li>모델은 선택된 데이터를 통해 보상함수<code>r(y)</code>를 학습함</li>
<li>결국 사람이 선호활 확률이 높은 답변일수록 보상 점수가 높게 되도록 학습시키는 과정<h4 id="ppopolicy-optimization">PPO(Policy Optimization)</h4>
</li>
<li>보상함수를 이용하여 모델이 보상을 최대화하도록 강화학습(PPO)을 진행하는 과정</li>
<li>$L^{CLIP}(\theta) = -E_t[\min\left(r_{t}(\theta) A_{t}, \text{clip}(r_{t}(\theta), 1-\epsilon, 1+\epsilon) A_{t}\right)]$: PPO 손실 함수</li>
<li>$A_t = R_t - V_\phi(s_t)$: 현재 행동이 편균보다 얼마나 좋은지 나타내는 이득(advantage) 함수</li>
<li>$R_t =r_t+γr_{t+1}+γ^2r_{t+2}+…$: 시점 t에서 이후로 얻게 될 모든 보상의 누적 합(총 보상)</li>
<li>Critic: 현재 상태가 얼마나 좋은지를 예측하는 평가자 역할을 하는 모델, Value Function(값 함수)을 근사하는 신경망</li>
<li>$V_ϕ(s_t) = value,function$: 현재 상태에서 앞으로 받을 보상의 기대값을 예측하는 함수, 수학적으로는 <code>value function</code>, 신경망으로 구현하면 <code>critic</code> 네트워크의 출력값<h3 id="--결론">- 결론</h3>
</li>
<li>답변이 인간의 선호를 반영하게 되며, 유용한 답변이 생성 가능하게 됨</li>
<li>하지만 보상 모델 구축 비용이 크고, 튜닝(PPO과정)의 어려움으로 인해 학습이 불안정해지며, 데이터 편향의 위험성이 존재함<h2 id="c-dpodirect-preference-optimization">c. DPO(Direct Preference Optimization)</h2>
<h3 id="--개요-1">- 개요</h3>
</li>
<li>인간이 선호하는 답변을 직접적으로 반영하여 모델을 학습시키는 방법</li>
<li>기존의 RLHF처럼 RM, PPO를 사용하지 않고 단순히 사람이 좋아한 답변과 싫어한 답변만으로 직접 선호도를 반영하여 모델을 정렬시키는 과정</li>
<li>강화학습의 한 종류지만 PPO와 같은 강화학습을 사용하지 않음<h3 id="--전체-학습-구조-1">- 전체 학습 구조</h3>
</li>
<li>학습 과정이 SFT -&gt; DPO 학습 단계로 구성됨
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/44747ea7-f757-4eae-a956-1ec735769454/image.png" /><h3 id="--기본-데이터-구조-1">- 기본 데이터 구조</h3>
</li>
<li>데이터 형식: <code>(prompt, chosen, rejected)</code></li>
<li><code>prompt</code>: $x$</li>
<li><code>chosen</code>: $y^+$</li>
<li><code>rejected</code>: $y^-$</li>
<li>인간 피드백 데이터에서 만들어짐<h3 id="--수식손실-함수">- 수식(손실 함수)</h3>
</li>
<li>$\mathcal{L}<em>{\text{DPO}}(\theta) = - \mathbb{E}</em>{(x, y_+, y_-)} \left[ \log \sigma \left( \beta \left( \log\pi_{\theta}(y_+|x) - \log\pi_{\theta}(y_-|x) \right) - \beta \left( \log\pi_{\text{ref}}(y_+|x) - \log\pi_{\text{ref}}(y_-|x) \right) \right) \right]$</li>
<li>실제 목표는 함수값을 최대화 하는 것이 목표지만 컴퓨터의 학습 알고리즘은 최소화가 목표이기 때문에 수식 앞에 <code>-</code>가 붙음</li>
<li>참조 모델($\pi_\text{ref}$)에 비해 현재 모델($\pi_\theta$)의 선호도가 얼마나 더 올바른 방향으로 개선되었는갸를 측정함</li>
<li>시그모이드($\sigma$)함수를 통해 선호도를 이진 분류 문제로 변환(분수(나눗셈) 계산을 피하기 위해 log 사용)
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/a0841484-9557-430c-9b10-6d497fb193b5/image.png" /><h3 id="--결론-1">- 결론</h3>
</li>
<li>RLHF의 PPO 단계를 간단한 로지스틱 비교 손실로 대체한 방식</li>
<li>단순하고 효율적임</li>
<li>하지만 두 답변<code>(chosen, reject)</code>의 상대적 비교만 학습을 진행하기 때문에, 답변이 둘 다 별로더라도 한쪽 답변이 상대적으로 좋게 나오면 그쪽으로 학습이 진행될 가능성 존재함</li>
<li>데이터 품질에 민감하며, 선호 데이터가 일관되지 않거나 편향되어 있으면, 모델이 그 편향을 그대로 학습함</li>
<li>학습이 기준(reference) 모델에 의존적이라서 기존 모델이 나쁘면 DPO로 모델을 크게 개선하기 어려움</li>
<li><code>(prompt, chosen, rejected)</code>쌍만 학습하기 때문에 새로운 표현이나 답변 패턴을 발견하기 어려움</li>
<li>단순함으로 인해 &quot;부분적 선호&quot;나 &quot;세밀한 보상 분포&quot;를 표현아기 어려움(예: &quot;사실성은 좋지만 말투가 거칠음&quot;)</li>
<li>결론적으로 학습 안성성과 효율성 면에서는 뛰어나지만 정교한 alignment 품질은 RLHF보다 낮게 나올 수 있음(추론 능력, 창의적 응답 포함)<h2 id="c-grpogroup-relative-policy-optimization">C. GRPO(Group Relative Policy Optimization)</h2>
<h3 id="--개요-2">- 개요</h3>
</li>
<li>딥시크가 직접 개발</li>
<li>RLHF와 달리 보상 함수를 배우지 않고 같은 질문에 대한 여러 답변 간의 상대적 우열만으로 모델을 업데이이트 하는 방법</li>
<li>LLM의 수학/추론 능력 향상을 위해 개발된 방법</li>
<li>각 프롬프트에 대해 여러 답변을 생성한 뒤, 그 답변 집단의 평균 및 편차를 이용하여 &quot;각 답변이 평균 대비 얼마나 좋은가&quot;를 계산하여 정책을 업데이트함</li>
<li>메모리 연산 효율이 PPO 대비 개선되며, 안정적인 학습을 목표로 개발됨<h3 id="--데이터-입력">- 데이터 입력</h3>
</li>
<li>입력: <code>prompt</code></li>
<li>출력: 단일 입력에 대한 모델이 만든 여러 개의 후보 응답 <code>[response1,response2, response3, response4, ...]</code></li>
<li>보상: 각 응답에 대한 보상 $R_\text{jk}$ 을 계산한 값 <code>[0.4, 0.3,...]</code><h3 id="--학습-구조">- 학습 구조</h3>
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/3320ae92-0620-4d21-ae16-3781cb9103c3/image.png" /><h3 id="--수식손실-함수-1">- 수식(손실 함수)</h3>
<h4 id="reward--advantage">reward &amp; advantage</h4>
</li>
<li>하나의 프롬프트 $s_j$에 대해 $G$개의 응답($a_\text{j1}, a_\text{j2}, ...$)을 생성함</li>
<li>각각의 응답에 대한 보상 $R_\text{jk}$을 얻고, 보상을 바탕으로 그룹 평균과 표준편차로 정규화된 advantage 를 계산함</li>
<li>advantage: 이 행동이 평균보다 얼마나 더 좋은가를 나타내는 값, 보상 그 자체가 아니라 상대적인 우위를 뜻함</li>
<li>그룹 평균: $\bar{R}<em>j = \frac{1}{G} \sum</em>{k=1}^G R_{jk}$</li>
<li>표준편차로 정규화된 advantage: $A_{jk} = \frac{R_{jk} - \bar{R}_j}{\sigma_j + \epsilon}$</li>
</ul>
<h4 id="정책-업데이트">정책 업데이트</h4>
<ul>
<li>정책 업데이트 시 현재 정책($\pi_\theta$)과 이전 정책($\pi_{\theta_{old}}$)의 확률비를 사용함(PPO-style ratio)</li>
<li>현재 정책이 과거 정책보다 행동 $a_{jk}$를 얼마다 더(덜) 선택하려 하는지를 나타내는 비율</li>
<li>$r_{jk}(\theta) = \frac{\pi_\theta(a_{jk}|s_j)}{\pi_{\theta_{old}}(a_{jk}|s_j)}$</li>
<li>비율이 너무 커지면(정책이 급격히 바뀌면) 학습이 불안정해지므로 클리핑(clipping)으로 제한</li>
</ul>
<h4 id="ppo-style-clipping을-적용한-grpo-loss">PPO-style Clipping을 적용한 GRPO Loss</h4>
<ul>
<li>$$L^{\text{GRPO}}(\theta) = -\frac{1}{J} \sum_{j=1}^{J} \frac{1}{G} \sum_{k=1}^{G} \min\left(r_{jk}(\theta) A_{jk}, \text{clip}(r_{jk}(\theta), 1-\epsilon, 1+\epsilon) A_{jk}\right) + \beta D_{\text{KL}}\left(\pi_\theta(\cdot | s_j) | \pi_{\text{ref}}(\cdot | s_j)\right)$$</li>
<li>$J$: 프롬프트 개수</li>
<li>$clip(r_{jk}(\theta), 1-\epsilon, 1+\epsilon)$: $r$이 너무 커지거나 작아지는 것을 막기 위해 정책 비율울 $[1-\epsilon, 1+\epsilon]$ 사이로 제한함</li>
<li>$min()$: 두 결과 중에서 값이 작은, 보수적인, 안전한 업데이트 선택<h3 id="--결론-2">- 결론</h3>
</li>
<li>여러 <code>response</code>를 생성하고 각각 <code>reward</code>를 계산한 뒤, 그룹 내 상대 이득으로 <code>advantage</code>를 정의하고 확률비와 곱해 <code>Policy</code>를 업데이트하는 <code>critic</code>없는 <code>PPO</code> 구조</li>
<li>$GRPO = PPO - Critic + Group Normalization$</li>
<li>하지만 그룹 내 모든 응답이 나쁜 경우, 그룹 평균이 낮고 이득 계산이 어렵다는 문제 발생</li>
<li>잘못된 보상 설계가 학습 왜곡시킬 수 있음</li>
<li>여러 응답이 필요하므로, 탐색이나 응답 다양성이 부족하면 학습이 정체될 수 있음</li>
<li>value function이 존재하지 않아 미래 보상의 누적 효과나, 상태 가치를 반영하는 측면에서는 약할 수 있음</li>
</ul>
<hr />
<h1 id="2-3개-비교-정리">2. 3개 비교 정리</h1>
<table>
<thead>
<tr>
<th>구분</th>
<th><strong>PPO</strong></th>
<th><strong>GRPO</strong></th>
<th><strong>DPO</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>풀네임</strong></td>
<td><em>Proximal Policy Optimization</em></td>
<td><em>Group Relative Policy Optimization</em></td>
<td><em>Direct Preference Optimization</em></td>
</tr>
<tr>
<td><strong>학습 유형</strong></td>
<td>강화학습 (RLHF 핵심)</td>
<td>강화학습 (Critic 제거형)</td>
<td>지도학습 (선호 직접 최적화)</td>
</tr>
<tr>
<td><strong>기본 아이디어</strong></td>
<td>보상 함수를 이용해 policy를 강화</td>
<td>여러 응답의 상대적 보상을 이용</td>
<td>좋은 답변 vs 나쁜 답변의 확률 차이를 직접 최적화</td>
</tr>
<tr>
<td><strong>필요 데이터</strong></td>
<td>(prompt, response, reward)</td>
<td>(prompt, [responses], [rewards])</td>
<td>(prompt, chosen, rejected)</td>
</tr>
<tr>
<td><strong>보상(Reward)</strong></td>
<td>존재 (RM에서 계산)</td>
<td>존재 (RM 또는 규칙 기반)</td>
<td>없음 (선호 쌍으로 간접 반영)</td>
</tr>
<tr>
<td><strong>Value Function</strong></td>
<td>있음 — (V_\phi(s_t))</td>
<td>없음 (그룹 평균으로 대체)</td>
<td>없음</td>
</tr>
<tr>
<td><strong>Critic 네트워크</strong></td>
<td>있음 (Value Function 예측)</td>
<td>없음</td>
<td>없음</td>
</tr>
<tr>
<td><strong>Advantage 계산식</strong></td>
<td>(A_t = R_t - V_\phi(s_t))</td>
<td>(A_{jk} = (R_{jk} - \bar{R}_j)/\sigma_j)</td>
<td>없음</td>
</tr>
<tr>
<td><strong>기준(Baseline)</strong></td>
<td>Critic의 예상 값 (V_\phi)</td>
<td>그룹 평균 (\bar{R}_j)</td>
<td>없음</td>
</tr>
<tr>
<td><strong>Loss 구성</strong></td>
<td>(-E[\min(rA, clip(r)A)] - \beta D_{KL})</td>
<td>(-E[\min(rA, clip(r)A)] - \beta D_{KL})</td>
<td>(-E[\log \sigma(\beta[\log π(y⁺)-\log π(y⁻)] - Δ_{ref})])</td>
</tr>
<tr>
<td><strong>KL 제약(안정화)</strong></td>
<td>Clipping + KL penalty (선택적)</td>
<td>Clipping + KL penalty</td>
<td>명시적 KL 항 포함 ((\pi_{ref}))</td>
</tr>
<tr>
<td><strong>Critic 학습 목적</strong></td>
<td>( (V_\phi - R)^2 ) 최소화</td>
<td>없음</td>
<td>없음</td>
</tr>
<tr>
<td><strong>장점</strong></td>
<td>안정적 강화학습, 절대 보상 반영</td>
<td>Critic 없이 간결, 효율적</td>
<td>보상모델 불필요, 구현 간단</td>
</tr>
<tr>
<td><strong>단점</strong></td>
<td>Critic 학습 불안정, 계산량 큼</td>
<td>절대 보상 반영 어려움</td>
<td>장기적 보상 고려 불가, 단기 선호 중심</td>
</tr>
<tr>
<td><strong>학습 결과</strong></td>
<td>“보상 높은 답변” 생성</td>
<td>“그룹 내 상대적으로 좋은 답변” 생성</td>
<td>“인간이 더 선호한 답변” 생성</td>
</tr>
<tr>
<td><strong>대표 사용 사례</strong></td>
<td>InstructGPT, ChatGPT PPO 단계</td>
<td>DeepSeek, OpenVLA 등 연구형</td>
<td>Alpaca, Zephyr, LLaMA-DPO 등</td>
</tr>
<tr>
<td><strong>핵심 차이 요약</strong></td>
<td>Critic 기반 RL</td>
<td>Critic 제거형 RL</td>
<td>비-RL 선호 최적화</td>
</tr>
<tr>
<td>---</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td># 3. 한줄 요약</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>- PPO → “Reward + Value Function + Advantage”</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>- GRPO → “Reward + Group 평균 Advantage (Critic 제거)”</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>- DPO → “Reward 없이 선호쌍 직접 비교 (PPO 존재X)”</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody></table>
<hr />
<h1 id="4-olmocr이-dpr을-사용하지-않은-이유">4. olmOCR이 DPR을 사용하지 않은 이유</h1>
<ul>
<li>olmOCR의 목표는 전사 정확도 향상, 각 샘플마다 명확한 정답 존재</li>
<li>DPO는 보상 모델 없이 선호 데이터만으로 정책 모델을 학습시키는 방법</li>
<li>선호(preference) 기반 정렬학습 형태를 가진 DPO 구조는 불필요함</li>
<li>따라서 정학도(accuracy) 기반 강화학습 형태를 가지고 있는 GRPO가 olmOCR의 목적에 부합함</li>
</ul>
<table>
<thead>
<tr>
<th>항목</th>
<th>DPO</th>
<th>olmOCR</th>
</tr>
</thead>
<tbody><tr>
<td>학습 형태</td>
<td>선호쌍(preferred vs rejected)</td>
<td>정답(target) 존재</td>
</tr>
<tr>
<td>목적</td>
<td>선호도 정렬(preference alignment)</td>
<td>텍스트 전사 정확도(maximum likelihood)</td>
</tr>
<tr>
<td>보상 계산</td>
<td>사람의 선택 or 간접 피드백</td>
<td>유사도 기반 수치화(pass rate, BLEU, diff ratio)</td>
</tr>
<tr>
<td>적합한 Task</td>
<td>대화, 문장 개선, 스타일 조정</td>
<td>이미지→텍스트 변환, 구조적 인식</td>
</tr>
</tbody></table>