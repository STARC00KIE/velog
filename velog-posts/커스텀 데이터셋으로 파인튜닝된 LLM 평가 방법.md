<h1 id="1-정형-데이터나-분류-문제-중심의-머신러닝-평가-방법">1. 정형 데이터나 분류 문제 중심의 머신러닝 평가 방법</h1>
<h2 id="정확도accuracy">정확도(Accuracy)</h2>
<h2 id="f1-score">F1-Score</h2>
<hr />
<h1 id="2-전통적인-nlp-평가-방법">2. 전통적인 NLP 평가 방법</h1>
<h2 id="bleu-scorebilingual-evaluation-understudy"><strong>BLEU</strong> score(Bilingual Evaluation Understudy)</h2>
<ul>
<li>생성된 문장이 참조 문장의 단어를 얼마나 포함하고 있는지(정밀도)에 초점을 맞춤</li>
<li>추가로 연속된 n개의 단어 쌍(n-gram)의 일치도를 계산하여 기하평균을 냄</li>
<li>의미를 이해하지 못하므로, 의미가 전혀 다른 문장이여도 단어 구성이 비슷하면 높은 점수를 받을 수 있음<h2 id="rouge-scorerecall-oriented-understudy-for-gisting-evaluation"><strong>ROUGE</strong> score(Recall-Oriented Understudy for Gisting Evaluation)</h2>
</li>
<li>텍스트 요약 테스크에서 참조 요약문의 핵심 내용이 생성된 요약문에 얼마나 빠짐없이 포함되었는지를(재현율) 측정하기 위해 개발되었음</li>
<li>어휘적 중복에 의존하기 때문에 창의적인 표현을 사용할 경우 점수가 낮게 나옴<h3 id="공통적으로-복잡한-추론-능력이나-문맥적-뉘앙스를-포착하지-못함">공통적으로 복잡한 추론 능력이나 문맥적 뉘앙스를 포착하지 못함</h3>
</li>
</ul>
<hr />
<h1 id="3-최근-llm-평가-방법">3. 최근 LLM 평가 방법</h1>
<ul>
<li>임베딩 기반의 의미론적 평가</li>
<li>상위 모델이 하위 모델 평가(llm-as-a-judge)</li>
<li>인간 피드팩을 체계적으로 통합하는 방식(HITL)</li>
</ul>
<hr />
<h1 id="4-hugging-face-evaluate">4. Hugging Face Evaluate</h1>
<ul>
<li>BLEU, ROUGE 같은 레거시 지표들을 손쉽게 계산할 수 있는 인터페이스를 제공</li>
<li><a href="https://huggingface.co/docs/evaluate/index">https://huggingface.co/docs/evaluate/index</a></li>
</ul>
<hr />
<h1 id="5-bertscore">5. BERTScore</h1>
<ul>
<li>딥러닝 모델의 잠재 공간을 활용하여 문장의 의미적 유사성을 측정함</li>
<li>문장 내의 주변 단어들과의 관계를 고려한 동적 임베딩을 생성함</li>
<li><code>Word2Vec</code>이 아닌 문장 내의 주변 단어들과의 관계를 고려한 동적 임베딩</li>
<li><code>evaluate</code>, <code>bert_score</code> 패키지를 활용하여 쉽게 구현할 수 있음</li>
</ul>
<hr />
<h1 id="6-llm-as-a-judge">6. LLM-as-a-Judge</h1>
<ul>
<li>고성능 LLM을 심판으로 활용하여 파인튜닝된 모델의 출력을 평가하는 방식</li>
<li>크게 두 가지 방식으로 구현됨<ul>
<li>점수 기반 평가: 고성능 LLM이 모델의 답변 하나를 독립적으로 평가하여 절재거인 점수 푸여</li>
<li>쌍별 비교 평가: 두 모델의 답변을 동시에 제시하고, 답변들의 우위를 평가</li>
<li>모델 간의 미세한 우위를 판별하는데 유리함</li>
</ul>
</li>
<li><code>judges</code>라이브러리나 OpenAI API를 활용하여 구현이 가능함<h2 id="문제점편향-문제">문제점(편향 문제)</h2>
</li>
<li>먼저 제시된 답변을 선호하거나 나중에 제시된 답변을 선호하는 경향이 있음</li>
<li>내용의 질보다 길이가 긴 답변을 선호하는 경향이 있음</li>
<li>평가자 모델이 생성한 답변과 유사한 스타일을 선호하는 경향이 있음</li>
</ul>
<hr />
<h1 id="7-deepeval">7. DeepEval</h1>
<ul>
<li>LLM을 지속적으로 테스트라고 검증하기 위해 필요한 전문 프레임워크</li>
<li>평가를 유닛 테스트를 개념으로 접근함</li>
<li>필요한 지표를 선택하여 테스트 케이스를 구성하고 이를 자동화된 스크립트로 실행할 수 있음<h2 id="주요-지표">주요 지표</h2>
</li>
<li><strong>HallucinationMetric</strong>: RAG나 파인튜닝 모델이 제공된 컨텍스트와 모순되는 내용을 생성하는지 검사함</li>
<li><strong>AnswerRelevancyMetric</strong>: 답변이 질문과 관련이 있는지 평가함</li>
<li><strong>FaithfulnessMetric</strong>: 답변이 사실에 충실한지 평가함</li>
<li><strong>G-Eva</strong>l: 사용자가 자연어로 정의한 커스텀 기준을 바탕으로 Chain-of-Thought(CoT) 방식을 사용하여 평가함</li>
</ul>
<hr />
<h1 id="8-ragasretrieval-augmented-generation-assessment">8. RAGAS(Retrieval Augmented Generation Assessment)</h1>
<ul>
<li>검색 증강 및 생성 품질 심층 분석에 사용됨</li>
<li>원래 RAG 시스템 평가를 위해 개발되었지만, 파인튜닝된 모델의 생성 품질을 평가하는 데에도 탁월한 성능을 발휘함</li>
<li>커스텀 데이터셋을 지식 베이스로 활용하는 모델일 경우, RAGAS의 지표들은 모델이 해당 지식을 어마나 정확하게 인출하고 활용하는 지 측정하는 잣대가 됨<h2 id="주요-지표-1">주요 지표</h2>
<h3 id="faithfulness충실성"><strong>Faithfulness(충실성)</strong></h3>
</li>
<li>모델의 답변이 주어진 문맥에서 유추 가능한 사실들로만 구성되어 있는지를 측정함</li>
<li>환각을 방지하고 사실적 일관성을 유지하는 데 필수적임</li>
<li>답변을 여러 개의 문장으로 분해하고, 각 문장이 컨텍스트에 의해 지지되는지 여불을 LLM으로 검증한 후 비율 계산</li>
<li>점수가 낮으면 모델이 학습 데이터를 제대로 기억하지 못하거나 외부 지식을 혼동하고 있음을 확인할 수 있음<h3 id="answer--relevancy답변-관련성"><strong>Answer  Relevancy(답변 관련성)</strong></h3>
</li>
<li>답변이 질문의 의도에 적합한지 측정함</li>
<li>생성된 답변을 바탕으로 역으로 질문을 생성해보고, 원본 질문과의 코사인 유사도를 비교함</li>
<li>유사도가 높을수록 답변이 질문의 핵심을 잘 담고 있음</li>
<li>점수가 낮으면 모델이 동문서답을 하고나 정황한 답변을 생성하고 있을 가능성이 높음</li>
</ul>
<hr />
<h1 id="9-hitlhuman-in-the-loop">9. HITL(Human-in-the-Loop)</h1>
<ul>
<li>MLOps 플랫폼인 Argilla를 이용하여 인간 피드백을 수집하고 관리함</li>
<li>또한 파인튜닝된 모델의 출력을 실시간으로 로깅하고 도메인 전문가들이 UI를 통해 이를 평가, 수정, 비교할 수 있는 통합 환경을 제공함</li>
<li>모델 모니터링을 할 수 있으며, 향후 RLHF/DPO 데이터셋 구축에 활용횜</li>
</ul>
<hr />
<h1 id="10-정리">10. 정리</h1>
<table>
<thead>
<tr>
<th align="left">단계</th>
<th align="left">평가 목적</th>
<th align="left">추천 도구 및 지표</th>
<th align="left">비고</th>
</tr>
</thead>
<tbody><tr>
<td align="left">1. Sanity Check</td>
<td align="left">학습 정상 여부 및 기본 문장력 검증</td>
<td align="left"><strong>HF Evaluate (BLEU, ROUGE)</strong></td>
<td align="left">오버피팅 여부 1차 필터링</td>
</tr>
<tr>
<td align="left">2. 의미론적 검증</td>
<td align="left">정답과의 의미적 유사성 및 의도 파악</td>
<td align="left"><strong>BERTScore</strong></td>
<td align="left">유의어, 패러프레이징 인식</td>
</tr>
<tr>
<td align="left">3. 심층 논리/안전성</td>
<td align="left">사실 관계(환각), 논리적 비약, 유해성 검증</td>
<td align="left"><strong>DeepEval, RAGAS (Faithfulness, Hallucination)</strong></td>
<td align="left">유닛 테스트 형태로 자동화</td>
</tr>
<tr>
<td align="left">4. 정성적 종합 평가</td>
<td align="left">창의성, 복합 추론, 뉘앙스 평가</td>
<td align="left"><strong>LLM-as-a-Judge (GPT-4)</strong></td>
<td align="left">MT-Bench 스타일의 심층 리포트</td>
</tr>
<tr>
<td align="left">5. 최종 사용자 검증</td>
<td align="left">실제 사용자 경험(UX) 및 도메인 적합성</td>
<td align="left"><strong>Argilla (Human Feedback)</strong></td>
<td align="left">RLHF/DPO를 위한 데이터 축적</td>
</tr>
</tbody></table>